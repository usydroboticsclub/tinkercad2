Plan
====

-   Using Servos

-   Using an Ultrasonic Sensor

-   Your Turn: Make a Touchless Covid Timer

# Recordings now available!
The password for these recordings is Kp94+cEGZyNe

The below links will expire on 06-11-2020 and will become unavailable for download after this date.

Audio Only (23.04 MB)
https://cloudstor.aarnet.edu.au/plus/s/JbtNJVqPkleFXeY

Video (233.18 MB)
https://cloudstor.aarnet.edu.au/plus/s/ci9qNQVp4BnEcIk

Other (1012.00 B)
https://cloudstor.aarnet.edu.au/plus/s/SQ8a8DUFlXCxbrd


Using Servos-
=============

**Equipment-**

-   1x Breadboard

-   1x Arduino

-   1x Servo

**Instructions-**

1.  Connect the ground and power pins to their respective branches on the breadboard to power the servo

2.  Connect the signal pin (orange wire) to pin 9 on the Arduino

3.  Copy the code below into the Arduino

**Schematic-**

![Schematic](https://github.com/usydroboticsclub/tinkercad2/blob/master/tink_1.png "Schematic")


**Code:**

\#include &lt;Servo.h&gt;

Servo myservo; // create servo object to control a servo

// twelve servo objects can be created on most boards

int pos = 0; // variable to store the servo position

void setup() {

myservo.attach(9); // attaches the servo on pin 9 to the servo object

}

void loop() {

for (pos = 0; pos &lt;= 180; pos += 1) { // goes from 0 degrees to 180
degrees

// in steps of 1 degree

myservo.write(pos); // tell servo to go to position in variable 'pos'

delay(15); // waits 15ms for the servo to reach the position

}

for (pos = 180; pos &gt;= 0; pos -= 1) { // goes from 180 degrees to 0
degrees

myservo.write(pos); // tell servo to go to position in variable 'pos'

delay(15); // waits 15ms for the servo to reach the position

}

}

Using an Ultrasonic Sensor-
===========================

**Equipment-**

-   1x Breadboard

-   1x Arduino

-   1x Ultrasonic Sensor

**Instructions-**

1.  Connect your VCC (Power) and GND pins on the sensor to their respective pins

2.  Connect Trig to pin 3

3.  Connect Echo to pin 2

**Schematic-**

![Schematic](https://github.com/usydroboticsclub/tinkercad2/blob/master/tink_2.png "Schematic")

**Code:**

// ---------------------------------------------------------------- //

// Arduino Ultrasoninc Sensor HC-SR04

// Re-writed by Arbi Abdul Jabbaar

// Using Arduino IDE 1.8.7

// Using HC-SR04 Module

// Tested on 17 September 2019

// ---------------------------------------------------------------- //

\#define echoPin 2 // attach pin D2 Arduino to pin Echo of HC-SR04

\#define trigPin 3 //attach pin D3 Arduino to pin Trig of HC-SR04

// defines variables

long duration; // variable for the duration of sound wave travel

int distance; // variable for the distance measurement

void setup() {

pinMode(trigPin, OUTPUT); // Sets the trigPin as an OUTPUT

pinMode(echoPin, INPUT); // Sets the echoPin as an INPUT

Serial.begin(9600); // // Serial Communication is starting with 9600 of
baudrate speed

Serial.println("Ultrasonic Sensor HC-SR04 Test"); // print some text in
Serial Monitor

Serial.println("with Arduino UNO R3");

}

void loop() {

// Clears the trigPin condition

digitalWrite(trigPin, LOW);

delayMicroseconds(2);

// Sets the trigPin HIGH (ACTIVE) for 10 microseconds

digitalWrite(trigPin, HIGH);

delayMicroseconds(10);

digitalWrite(trigPin, LOW);

// Reads the echoPin, returns the sound wave travel time in microseconds

duration = pulseIn(echoPin, HIGH);

// Calculating the distance

distance = duration \* 0.034 / 2; // Speed of sound wave divided by 2
(go and back)

// Displays the distance on the Serial Monitor

Serial.print("Distance: ");

Serial.print(distance);

Serial.println(" cm");

}

Additional Notes:

-   The real world, the ultrasonic sensor we’re using can measure from distances between 2-400cm with an accuracy of 3mm

-   Speed of sound = 343m/s

    -   This is equivalent to 0.034 cm/μs

Your Turn-
==========

Your job is to create a timer for handwashing. The device will use an
ultrasonic sensor to detect the presence of hands, which will then
activate a servo that moves from 0 to 180 in 20 seconds.

Bonus Meme(Content)-
====================

Diagram of LCD-

![TDiagram of LCD](https://github.com/usydroboticsclub/tinkercad2/blob/master/tink_4.png "Diagram of LCD")

**Explanation of each pin-**

-   GND and VCC-Provide power to the display

-   V0- Used to control the contrast between the images on the screen based upon the voltage input

-   RS- Used to determine whether we send commands or data to the LCD. If the input into RS is LOW, then we are sending commands into the LCD (eg. Set cursor to specific location). If the input into RS is HIGH, then we are sending data or characters into the LCD

-   R/W- Selects whether we are reading or writing to the LCD. Writing to the LCD means we are providing data into the display (commands or characters). Reading refers to extracting information from the LCD itself, and is done by the LCD as we execute the program.

-   E- Enables writing to the registers, or the next 8 data pins

-   D0-D7- Data pins for the LCD. These pins can take up to 8 bits of data in order to display a character based on the ASCII table

-   A and K- Anode and Cathode for the LED back light

**Equipment-**

-   1x Arduino

-   1x Breadboard

-   1x LCD

-   1x Potentiometer

Using an LCD-
=============

1.  Connect VCC and GND of the LCD to their respective pins

2.  Connect the V0 pin of the LCD to the output pin of a pontetiometer. This will be used to control the contrast of the screen display

3.  Connect RS pin to pin 1

4.  Connect R/W pin to GND

5.  Connect Enable pin to pin 2

6.  Connect digital pins D7, D6, D5 and D4 on the LCD to pins 7,6,5 and 4 respectively on the Arduino

7.  Connect the anode pin to Power and the cathode to GND

![TDiagram of LCD](https://github.com/usydroboticsclub/tinkercad2/blob/master/tink_5.png "Diagram of LCD")

Code:

 /\*

 \* Arduino LCD Tutorial

 \*

\* Crated by Dejan Nedelkovski,

\* www.HowToMechatronics.com

\*

\*/

 \#include &lt;LiquidCrystal.h&gt; // includes the LiquidCrystal
    > Library

 LiquidCrystal lcd(1, 2, 4, 5, 6, 7); // Creates an LC object.
    > Parameters: (rs, enable, d4, d5, d6, d7)

 **void** setup() {

 lcd.begin(16,2); // Initializes the interface to the LCD screen, and
    > specifies the dimensions (width and height) of the display }

}

 **void** loop() {

 lcd.print("Arduino"); // Prints "Arduino" on the LCD

delay(3000); // 3 seconds delay

lcd.setCursor(2,1); // Sets the location at which subsequent text written to the LCD will be displayed

lcd.print("LCD Tutorial");

delay(3000);

lcd.clear(); // Clears the display

lcd.blink(); //Displays the blinking LCD cursor

delay(4000);

lcd.setCursor(7,1);

delay(3000);
lcd.noBlink(); // Turns off the blinking LCD cursor

lcd.cursor(); // Displays an underscore (line) at the position to which the next character will be written

delay(4000);

lcd.noCursor(); // Hides the LCD cursor

lcd.clear(); // Clears the LCD screen
}


