
#include <Servo.h>
  Servo ylservo;
  Servo zlservo;
#define youchuan  4
#define zuochuan  7
const int Trig = 2;
const int Echo = 3;
float cm;


void setup() {
  pinMode(Trig, OUTPUT);
  pinMode(Echo, INPUT);
  pinMode(zuochuan, INPUT);
  pinMode(youchuan, INPUT);
  zlservo.attach(9);
  ylservo.attach(12);
  Serial.begin(9600);
}



void ceju()
{
  digitalWrite(Trig,LOW);
  delayMicroseconds(2);
  digitalWrite(Trig,HIGH);
  delayMicroseconds(10);
  digitalWrite(Trig,LOW);
  cm =pulseIn(Echo,HIGH)/58;
  Serial.print(cm);
  Serial.print("cm");
  Serial.println();
  delay(50);
 
}


  // put your setup code here, to run once:




void loop()
 {
   int zc = analogRead(7);
   int yc = analogRead(4);
   ceju();
   Serial.println(zc);
   Serial.println(yc);

   if(zc<100 && yc<100)
  {

    zlservo.writeMicroseconds(1000); 
    ylservo.writeMicroseconds(2000);
    delay(50);
  }
  else if(zc>=100 && yc<100)
  {

    zlservo.writeMicroseconds(1500); 
    ylservo.writeMicroseconds(2000);  
    delay(50);
  }
  else if(zc<100 && yc>=100)
  {
    zlservo.writeMicroseconds(1000); 
    ylservo.writeMicroseconds(1500);
    delay(50);
  
  // put your main code here, to run repeatedly:
  }
  else if(zc>=100 && yc>=100)
  {
    zlservo.writeMicroseconds(1000); 
    ylservo.writeMicroseconds(2000);
    delay(50);
  }
  else if(cm<=12)
  {

    zlservo.writeMicroseconds(1500); 
    ylservo.writeMicroseconds(2000);
    delay(1350);
    zlservo.writeMicroseconds(1000); 
    ylservo.writeMicroseconds(2000);
    delay(500);
    zlservo.writeMicroseconds(1000); 
    ylservo.writeMicroseconds(1500);
    delay(1500);
    zlservo.writeMicroseconds(1000); 
    ylservo.writeMicroseconds(2000);
    delay(1000);
    zlservo.writeMicroseconds(1000); 
    ylservo.writeMicroseconds(1500);
    delay(1500);    
    zlservo.writeMicroseconds(1000); 
    ylservo.writeMicroseconds(2000);
    delay(500);
    zlservo.writeMicroseconds(1500); 
    ylservo.writeMicroseconds(2000);
    delay(1500);
    

  }
}
