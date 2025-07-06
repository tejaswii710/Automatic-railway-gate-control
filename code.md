## Arduino Code: Automatic Railway Gate Control with 2 IR Sensors

```

#include <Servo.h>

int ir1 = 2;
int ir2 = 7;

Servo gateServo;

void setup()
{
    pinMode(ir1, INPUT);
    pinMode(ir2, INPUT);
    pinMode(13, OUTPUT); // LED
    pinMode(12, OUTPUT); // BUZZER
    pinMode(11, OUTPUT); // LED
    pinMode(10, OUTPUT); // LED
    pinMode(9, OUTPUT);  // LED

    gateServo.attach(3); // Servo connected to pin 3

    // Start with gate open
    gateServo.write(0);
}

void loop()
{
    if (digitalRead(ir1) == LOW)
    {
        gateServo.write(90); // Close gate

        digitalWrite(13, HIGH); // LED
        digitalWrite(12, HIGH); // BUZZER
        digitalWrite(11, LOW);  // LED
        digitalWrite(10, LOW);  // LED
        digitalWrite(9, HIGH);  // LED
    }
    else if (digitalRead(ir2) == LOW)
    {
        gateServo.write(0); // Open gate

        digitalWrite(13, LOW);  // LED
        digitalWrite(12, LOW);  // BUZZER
        digitalWrite(11, HIGH); // LED
        digitalWrite(10, HIGH); // LED
        digitalWrite(9, LOW);   // LED
    }
}

