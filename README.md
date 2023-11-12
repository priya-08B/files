  IOT-Project: Public Transport Optimization
Abstract Idea:
Transit Sense is an IOT project revolutionizing urban public transportation by leveraging real-time data and advanced analytics. Through a network of IOT sensors on vehicles and at transit stops, it predicts passenger demand, optimizes routes, and provides passengers with personalized journey recommendations. Real-time information and eco-friendly transportation options enhance the passenger experience, while traffic management reduces congestion and emissions. Transit Sense aims to create efficient, sustainable, and user-centric public transportation systems, improving urban mobility and reducing environmental impact.

Design Thinking Process:

Design Thinking is a user-centric problem-solving methodology that can be applied to IOT-based public transport optimization to ensure that solutions are not only technologically advanced but also align with the needs and experiences of passengers and stakeholders. Here's how to apply the Design Thinking approach to this context:

1. Empathize:
   - Understand the needs, pain points, and preferences of passengers by conducting interviews, surveys, and observations at transport hubs.
   -  Collaborate with transit authorities, operators, and local communities to gather insights and perspectives on public transport challenges.

2. Define:
   - Define the specific challenges within the public transport system, such as overcrowding, delays, or accessibility issues, based on the insights gathered during the empathy phase.
   -  Create user personas representing different passenger segments to guide solution development.
3. Ideate:
   -  Organize ideation workshops with a diverse group of stakeholders to generate creative ideas for addressing the identified problems.
  - Focus on features that enhance the passenger experience, such as real-time information, accessibility features, and sustainable transportation options.

4. Prototype:
   -  Develop low-fidelity prototypes of IOT-based solutions, including mobile apps, sensor networks, or data dashboards, to visualize how they would work.
   -  Gather feedback from passengers and stakeholders by conducting usability testing with the prototypes to refine the design.

5. Test:
   -  Implement a small-scale pilot of the IOT solution on a specific public transport route or mode to assess its effectiveness in a real-world setting.
   -  Collect data on passenger satisfaction, system performance, and environmental impact during the pilot phase.

6. Implement:
   -  If the pilot is successful, scale up the IOT solution to cover a larger portion of the public transport network.
   - Collaborate closely with transit authorities and operators to integrate the IOT solution into existing systems.

7. Evaluate and Iterate:
   - Continuously collect user feedback and monitor system performance to identify areas for improvement.
   - Use iterative development cycles to refine and enhance the IOT-based solution based on ongoing feedback and changing needs.

By applying the Design Thinking approach, IOT-based public transport optimization becomes a user-centered and iterative process. This approach ensures that the solutions implemented are not only technologically advanced but also genuinely address the needs and preferences of passengers while promoting efficiency, sustainability, and accessibility in urban transportation.


PHASE 2:
 PUBLIC TRANSPORT OPTIMIZATION

INNOVATION 

Innovations for public transport optimization can greatly improve efficiency, accessibility, and sustainability. Here are some key innovations in this area.

Step1: Introduction

Overview 

The "Transit Sense" IOT project is aimed at revolutionizing urban public transportation through real-time data and advanced analytics. It focuses on optimizing public transport routes, enhancing passenger experiences, reducing congestion, and promoting eco-friendly transportation options.

Objective

This document outlines the step-by-step process of incorporating machine learning algorithms into the "Transit Sense" project to improve the accuracy of arrival time predictions. This enhancement will provide passengers with more reliable and timely information, ultimately improving the overall transit experience.

Step2: Data Collection and Preparation

 Gather Historical Data: 

 Detailed explanation of collecting historical data on public transport routes, including departure times, actual arrival times, traffic conditions, and weather data.

Data Preprocessing:

 How to clean and preprocess the dataset, handling missing values,outliers, and data cleaning techniques.

Feature Engineering: 

 Creating meaningful features for machine learning, including time-related features and conversion of categorical variables.
 
 Real-Time Data Integration: 

 Developing a real-time data pipeline to provide current traffic conditions, weather updates, and vehicle locations to the machine learning model.

Step 3: Machine Learning Model Development 

 Model Selection: 

 Explanation of selecting an appropriate machine learning algorithm. (e.g., Random Forest, Gradient Boosting, LSTM) for 
arrival time prediction.
 
 Model Training: 

 How to split the dataset into training and testing sets and train the machine learning model using historical data.
 Model Evaluation: 

 Metrics and methods for evaluating the model's accuracy and performance, including MAE and RMSE.

Step 4: Real-Time Integration and Passenger Access

 Real-Time Data Integration: 

 Implementing a real-time data pipeline to feed current traffic conditions, weather updates, and vehicle locations to the machine learning model.

 Integration with Passenger Information Systems: 

 How to incorporate the machine learning model into passenger information systems, making predictions accessible to passengers through mobile apps and information displays.

Step 5: Feedback Loop and Continuous Improvement

Feedback Mechanism:

 Creating a feedback mechanism for passengers to report inaccuracies in arrival time predictions.
 
 Model Update and Iteration:

 How to use passenger feedback to continuously update and refine the machine learning model, ensuring its accuracy and 
responsiveness.

Step 6: Conclusion

Summary of how the integration of machine learning improves arrival time predictions, benefiting both passengers and the public transport system.


PHASE 3 - PUBLIC TRANSPORT OPTIMIZATION


INTRODUCTION

Optimizing public transport using Arduino is an exciting project. Simulating the behavior of hardware components like ultrasonic sensors in software can be done 
through virtual platforms. In this phase the system includes components such as ESP32 Development Board, Ultrasonic Sensors (2x), LED, Blynk App, Resistors and 
Wires. Here are the steps to simulate code using Wokwi.


COMPONENTS

1. ESP32 Development Board : powerful microcontroller board.

2. Ultrasonic Sensors (2x): Ultrasonic sensors are used for distance measurement. 

3. LED: An LED (Light Emitting Diode) is used as a visual indicator. 

4.Resistors and Wires: Resistors to limit the current flowing through the LED (typically a 220-330 ohm resistor) and jumper wires to connect the components on the breadboard.


5.Blynk App: The Blynk app is required to visualize the data and control the system remotely.


PROCEDURE: 

1. Software: Install Arduino IDE on your computer.

2. Board Support:

 - Open Arduino IDE.

 -Add ESP32 board and Install ESP32 board package via Tools > Board > Boards Manager.

- Select "ESP32 Dev Module".

3.Upload Code:

 - Copy and paste your modified code.

 - Click Upload to compile and upload the code to your ESP32 board.

#define BLYNK_TEMPLATE_ID "TMPL26V4fGv5q"

#define BLYNK_TEMPLATE_NAME "Test"

#define BLYNK_AUTH_TOKEN "XEHxNF_Ur1Nt2p7wB5B20dNI1ZUwj34P"

#include <WiFi.h>

#include <WiFiClient.h>

#include <BlynkSimpleEsp32.h>

int duration1 = 0;

int distance1 = 0;

int duration2 = 0;

int distance2 = 0;

int dis1 = 0;

int dis2 = 0;

int dis_new1 = 0;

int dis_new2 = 0;

int entered = 0;

int left = 0;

int inside = 0;

#define LED 2

#define PIN_TRIG1 15

#define PIN_ECHO1 14

#define PIN_TRIG2 13

#define PIN_ECHO2 12

BlynkTimer timer;

char auth[] = BLYNK_AUTH_TOKEN;

char ssid[] = "Wokwi-GUEST"; // your network SSID (name)char pass[] = "";

#define BLYNK_PRINT Serial

long get_distance1() {

// Start a new measurement:

digitalWrite(PIN_TRIG1, HIGH);delayMicroseconds(10);

digitalWrite(PIN_TRIG1, LOW);

// Read the result:

duration1 = pulseIn(PIN_ECHO1, HIGH);

distance1 = duration1 / 58;

return distance1;

}

long get_distance2() {

// Start a new measurement:

digitalWrite(PIN_TRIG2, HIGH);

delayMicroseconds(10);

digitalWrite(PIN_TRIG2, LOW);

// Read the result:

duration2 = pulseIn(PIN_ECHO2, HIGH);

distance2 = duration2 / 58;

return distance2;

}

void myTimer() {

Serial.println("100");

dis_new1 = get_distance1();

dis_new2 = get_distance2();

if (dis1 != dis_new1 || dis2 != dis_new2){

Serial.println("200");

if (dis1 < dis2){

Serial.println("Enter loop");

entered = entered + 1;

inside = inside + 1;

digitalWrite(LED, HIGH);

Blynk.virtualWrite(V0, entered);

Blynk.virtualWrite(V2, inside);

dis1 = dis_new1;

delay(1000);

digitalWrite(LED, LOW);

}

if (dis1 > dis2){

Serial.println("Leave loop");

left = left + 1;

inside = inside - 1;

Blynk.virtualWrite(V1, left);

Blynk.virtualWrite(V2, inside);

dis2 = dis_new2;delay(1000);

}

}

}

void setup() {

Serial.begin(115200);

pinMode(LED, OUTPUT);

pinMode(PIN_TRIG1, OUTPUT);

pinMode(PIN_ECHO1, INPUT);

pinMode(PIN_TRIG2, OUTPUT);

pinMode(PIN_ECHO2, INPUT);

Blynk.begin(auth, ssid, pass, "blynk.cloud", 8080);

timer.setInterval(1000L, myTimer);

}

void loop() {

Blynk.run();

timer.run();

}

3.Hardware Setup:

 - Connect ultrasonic sensors to PINs 15, 14, 13, and 12 for TRIG1, ECHO1, TRIG2, and ECHO2 respectively.

 - Connect an LED's long leg to PIN 2 and short leg to ground.

4. Blynk Setup:

 - Download Blynk app on your smartphone and Create a new project.

 - Set device to "ESP32 Dev Board".

 - Obtain Auth Token via email and replace it.
  
5.Testing:

  -Add widgets for Virtual Pins V0, V1, and V2 to visualize the entered count, left count, and inside count
respectively.

 - LED on PIN 2 will indicate entry (ON) or exit (OFF).

 - Check Serial Monitor (Tools > Serial Monitor) for debug messages and sensor readings.

Simulation

Code implementation: implemented the Arduino code to optimize the public transport level.

![image](https://github.com/priya-08B/files/assets/146112760/13f8a39a-d4dc-49e3-bae1-230742891da0)

Simulation: clicked the “simulate” button in Wokwi to start the simulation.


CONCLUSION

The presented project showcases a practical implementation of an object detection system using ESP32 microcontroller and ultrasonic sensors, facilitated 
by the Blynk IoT platform. 

In conclusion, this project exemplifies the seamless integration of hardware,software, and IoT technologies to create an efficient object detection and 
counting system. By leveraging the power of the ESP32 microcontroller and Blynk platform, it exemplifies the potential of IoT solutions in real-world applications,offering a glimpse into the future of smart, responsive systems.
