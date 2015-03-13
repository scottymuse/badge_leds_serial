badge_leds_serial

A program to be used on the SaintCON2014 badge

AUTHOR: Scott Nielsen (scotty)

Thanks to Klint Holmes. I used a lot of his original badge code here and to learn this stuff.
And Thanks to Luke Jenkins, Klint Holmes, Matt Lorimer, and Jonathan Karras for these badges!

To use:
Load this program onto the SaintCON 2014 badge. This does not require any additional hardware.
To run, connect the badge via USB to your computer, run your favorite serial terminal.
Use the same settings used in the 'Hack the badge' challenges at the con.
baud = 115200
data bits = 8
stop bits = 1
parity = None
Flow control = xon/xoff

The menu presented offers options of controlling the leds around the name plate.

The neat thing about this program is the leds are entirely controlled by timer interrupts
on the processor, leaving the main loop to run the serial interface.

My next steps on this project are to include a button on the badge to toggle through the
display options, and a potentiometer connected to an analog input to control the speed.
That will allow entire removal of the serial interface (everything in the 'void loop()')
and you can then run whatever program you want and still have the control over the led
blinking pattern.

A known issue is the interrupts are controlled by a timer on the processor which when used
disables the PWM ability on some of the pins. Specifically in this program, the pins
controlling the top leds on the name plate are affected, removing their ability to fade
easily with analogWrite(). So I do not include the top leds in the fade patterns.

IMPORTANT TIP: If you want to monkey with this code and load it onto your badge, make sure
you kill your serial connection before you push the code to the badge. You get some strange,
even somewhat frightening, errors sometimes if the serial connection is open.
