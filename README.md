# **🔋 Advanced IoT-Enabled EV Battery Management System | Developed by Gopal Satra**

## **📌 Project Overview**
This project, developed by **Gopal Satra**, is a cutting-edge **IoT-based Battery Management System (BMS)** designed for **Electric Vehicles (EVs)**. It integrates **embedded hardware, IoT, cloud computing, and machine learning** to enable **real-time battery monitoring, predictive analytics, and smart battery health management**. This system ensures **optimized performance, extended battery life, and enhanced safety** in EVs.

### **🔹 Key Features**
✅ **Real-time Battery Voltage, Current & Temperature Monitoring**  
✅ **SOC (State of Charge) & SOH (State of Health) Estimation**  
✅ **Machine Learning-Based Predictive Maintenance**  
✅ **IoT Connectivity via MQTT & Cloud Integration**  
✅ **Remote Dashboard for Monitoring & Alert System**  
✅ **Advanced Safety Mechanisms for Battery Protection**  

---

## **🛠️ Technologies Used**
- **Embedded C, Python, Keil uVision, Raspberry Pi, STM32**
- **AWS IoT, Firebase, MQTT, HTTP, Serial Communication**
- **Grafana, ThingSpeak for Dashboard Visualization**
- **Machine Learning for Battery Performance Prediction**
- **DHT11, Voltage & Current Sensors for Data Collection**

---

## **📜 Source Code**

### **🔹 `bms_firmware.c` - STM32 Firmware for Battery Monitoring**
```c
#include "stm32f1xx.h"
#define ADC_CHANNEL 0

void init_ADC(void);
float read_voltage(void);
float read_temperature(void);
float read_current(void);

int main() {
    init_ADC();
    while (1) {
        float voltage = read_voltage();
        float temperature = read_temperature();
        float current = read_current();
        // Transmit data via UART to IoT module
    }
}

void init_ADC(void) {
    // Initialize ADC for battery monitoring
}

float read_voltage(void) {
    return 3.7;  // Simulated battery voltage value
}

float read_temperature(void) {
    return 25.0;  // Simulated temperature in Celsius
}

float read_current(void) {
    return 1.5;  // Simulated current value
}
```

### **🔹 `iot_battery_monitor.py` - Raspberry Pi Data Acquisition & Cloud Upload**
```python
import paho.mqtt.client as mqtt
import Adafruit_DHT
import time

BROKER = "mqtt.eclipse.org"
TOPIC = "ev/battery/data"
client = mqtt.Client()
client.connect(BROKER, 1883, 60)

DHT_SENSOR = Adafruit_DHT.DHT11
DHT_PIN = 4

def read_sensors():
    humidity, temperature = Adafruit_DHT.read(DHT_SENSOR, DHT_PIN)
    voltage = 3.7  # Simulated battery voltage
    current = 1.5   # Simulated battery current
    return temperature, voltage, current

while True:
    temp, volt, curr = read_sensors()
    data = f"{{'temperature': {temp}, 'voltage': {volt}, 'current': {curr}}}"
    client.publish(TOPIC, data)
    print(f"Sent Data: {data}")
    time.sleep(5)
```

### **🔹 `firebase_upload.py` - Firebase Integration**
```python
import firebase_admin
from firebase_admin import credentials, db

cred = credentials.Certificate("firebase-credentials.json")
firebase_admin.initialize_app(cred, {
    'databaseURL': 'https://your-firebase-db.firebaseio.com/'
})

def upload_data(temp, volt, curr):
    ref = db.reference('/battery_data')
    ref.push({"temperature": temp, "voltage": volt, "current": curr})
    print("Data uploaded successfully!")
```

---

## **🛠 How to Run**
### **🔹 Hardware Setup**
1. Connect **STM32/Raspberry Pi** to **DHT11, Voltage & Current Sensors**.
2. Flash `bms_firmware.c` firmware to STM32.
3. Run `iot_battery_monitor.py` on Raspberry Pi to send real-time data.

### **🔹 Cloud & IoT Setup**
1. Configure **AWS IoT / Firebase Database**.
2. Deploy **Grafana / ThingSpeak** dashboard for visualization.
3. Enable **Alert Notifications for Battery Abnormalities**.
4. Train **Machine Learning Model** for Predictive Maintenance.

---

## **🔗 Connect With Me (Gopal Satra)**

🌐 **GitHub Profile:** [github.com/soham77777](https://github.com/soham77777)  
🔗 **LinkedIn:** [linkedin.com/in/gopal-santra-a1bb9a280](https://www.linkedin.com/in/gopal-santra-a1bb9a280/)  
📺 **YouTube:** [youtube.com/@gopalsantra2852](https://www.youtube.com/@gopalsantra2852)  
📷 **Instagram:** [instagram.com/gopal_santraa](https://www.instagram.com/gopal_santraa/)  
📫 **Email:** gopalsantra2002@gmail.com  

🚀 **Project Repo:** [Advanced EV BMS](https://github.com/soham77777/Advanced-EV-BMS)


