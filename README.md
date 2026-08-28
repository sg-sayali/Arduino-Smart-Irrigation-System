# 🌱 Smart Irrigation System using Arduino and Machine Learning

## 📌 Overview

The **Smart Irrigation System** is an automated plant watering and monitoring system developed using **Arduino Uno, sensors, a relay module, a water pump, and Bluetooth communication**.

The system monitors important environmental parameters such as **soil moisture, temperature, humidity, and water level**. Based on the soil moisture condition, the Arduino automatically controls the water pump through a relay.

An **HC-05 Bluetooth module** is used to transmit real-time sensor information to a mobile device.

In addition to the hardware-based automation, a **Random Forest Machine Learning model** is implemented using soil moisture, temperature, and humidity data to predict whether the plant needs watering.

The project focuses on **water conservation, automation, real-time monitoring, and intelligent irrigation**.

---

## 🎯 Objectives

- Automate the plant watering process.
- Detect whether the soil is dry or sufficiently moist.
- Monitor temperature and humidity using the DHT11 sensor.
- Monitor the water level of the reservoir.
- Automatically control the water pump using a relay.
- Send real-time sensor data to a mobile device using Bluetooth.
- Develop a Machine Learning model for watering prediction.
- Reduce water wastage and manual intervention.

---

## 🛠️ Hardware Components

- **Arduino Uno** – Main microcontroller
- **DHT11 Sensor** – Measures temperature and humidity
- **Soil Moisture Sensor** – Detects dry/wet soil condition
- **Water Level Sensor** – Monitors water level in the reservoir
- **Relay Module** – Controls the water pump
- **Mini Submersible Water Pump** – Supplies water to the plant
- **HC-05 Bluetooth Module** – Provides wireless communication
- Breadboard
- Jumper wires
- Power supply

---

## 💻 Software and Technologies

- Arduino IDE
- Embedded C/C++
- Python
- Pandas
- Scikit-learn
- Random Forest Classifier
- Machine Learning
- Bluetooth Communication

---

# 🔌 Circuit Connections

The following connections are used in the Arduino implementation:

| Component | Arduino Pin |
|---|---|
| Soil Moisture Sensor | Digital Pin 6 |
| Relay Module | Digital Pin 3 |
| DHT11 Sensor | Digital Pin 7 |
| Water Level Sensor | Analog Pin A0 |
| HC-05 RX | Digital Pin 8 |
| HC-05 TX | Digital Pin 9 |

### Pin Description

- **D6:** Reads the digital output of the soil moisture sensor.
- **D3:** Controls the relay connected to the water pump.
- **D7:** Receives DHT11 temperature and humidity data.
- **A0:** Reads the analog water-level sensor value.
- **D8/D9:** Used for serial communication with the HC-05 Bluetooth module.

---

# ⚙️ How the System Works

The system follows these steps:

1. Arduino reads the soil moisture sensor.
2. Arduino reads the water level sensor.
3. DHT11 measures temperature and humidity.
4. The soil condition is checked.
5. If the soil is detected as dry, the relay is activated and the water pump is turned ON.
6. If the soil has sufficient moisture, the relay is turned OFF and the pump remains OFF.
7. Sensor readings are displayed through the Serial Monitor.
8. Temperature, humidity, soil status, and water-level readings are transmitted through the HC-05 Bluetooth module.
9. The Machine Learning model uses soil moisture, temperature, and humidity values to predict whether watering is required.

---

# 🔄 System Flow

```text
          ┌─────────────────────┐
          │      Sensors        │
          │                     │
          │ Soil Moisture       │
          │ DHT11               │
          │ Water Level         │
          └──────────┬──────────┘
                     │
                     ▼
          ┌─────────────────────┐
          │     Arduino Uno     │
          │                     │
          │ Read Sensor Data    │
          │ Process Conditions  │
          └──────────┬──────────┘
                     │
              Soil Condition
                     │
          ┌──────────┴──────────┐
          │                     │
        DRY                   GOOD
          │                     │
          ▼                     ▼
   ┌─────────────┐       ┌─────────────┐
   │ Relay ON    │       │ Relay OFF   │
   └──────┬──────┘       └──────┬──────┘
          │                     │
          ▼                     ▼
   ┌─────────────┐       ┌─────────────┐
   │ Pump ON     │       │ Pump OFF    │
   └─────────────┘       └─────────────┘
                     │
                     ▼
          ┌─────────────────────┐
          │ HC-05 Bluetooth     │
          │ Mobile Monitoring   │
          └─────────────────────┘
```

---

# 🤖 Machine Learning Component

## Dataset

A synthetic dataset is used to train the Machine Learning model.

The dataset contains the following features:

| Feature | Description |
|---|---|
| `soil_moisture` | Soil moisture value |
| `temperature` | Temperature value |
| `humidity` | Humidity value |
| `water` | Target variable |

### Target

```text
water = 1 → Water the plant
water = 0 → Do not water the plant
```

---

## 🌲 Random Forest Model

A **Random Forest Classifier** is used to predict whether the plant requires watering.

### Model Configuration

```text
Algorithm       : Random Forest Classifier
Estimators      : 100
Random State    : 42
Training Data   : 80%
Testing Data    : 20%
```

### Input Features

The model uses:

```python
soil_moisture
temperature
humidity
```

### Preprocessing

`StandardScaler` is used to standardize the input features before training and prediction.

### Evaluation Metrics

The model is evaluated using:

- Confusion Matrix
- Precision
- Recall
- F1-Score
- Classification Report

---

# 🧪 Machine Learning Prediction

A sample input can be provided to the trained model:

```text
Soil Moisture = 20
Temperature   = 35°C
Humidity      = 45%
```

The model predicts whether the plant should be watered.

Example output:

```text
water the plant
```

or

```text
don't water the plant
```

---

# 📱 Bluetooth Monitoring

The **HC-05 Bluetooth module** is used to send sensor data from the Arduino to a mobile device.

The Arduino sends the data in a single line using the following format:

```text
Humidity,Temperature,Soil Status,Water Level
```

Example:

```text
55.00,30.00,DRY,420
```

This allows the user to monitor the system in real time through a Bluetooth-enabled mobile application.

---

# 💧 Water Pump Control

The water pump is controlled using a relay module.

The control logic implemented in the Arduino code is:

```text
If soil is DRY
        ↓
Relay ON
        ↓
Water Pump ON

If soil condition is GOOD
        ↓
Relay OFF
        ↓
Water Pump OFF
```

The water-level sensor is also monitored and its analog reading is transmitted to the user.

---

# 📷 Project Images

## 1. Complete Project Setup

![Complete Project Setup](images/project_setup.jpg)

## 2. DHT11 Temperature and Humidity Sensor

![DHT11 Sensor](images/DHT11_Temperature_Humidity.jpg)

## 3. HC-05 Bluetooth Module

![HC-05 Bluetooth Module](images/HC05_Bluetooth_Module.jpg)

## 4. Soil Moisture Sensor

![Soil Moisture Sensor](images/soil_moisture_sensor.jpg)

## 5. Water Level Sensor

![Water Level Sensor](images/water_level_sensor.jpg)

## 6. Relay Module

![Relay Module](images/relay_module.jpg)

## 7. Mini Submersible Water Pump

![Mini Submersible Water Pump](images/mini_submersible_water_pump.jpg)

## 8. Circuit Diagram

![Circuit Diagram](Circuit_Diagram.png)

---

# 📁 Project Structure

```text
Arduino-Smart-Irrigation-System
│
├── Smart_Irrigation.ino
├── ML_Model.py
├── smart_irrigation_data.csv
├── README.md
├── Circuit_Diagram.png
│
└── images
    ├── project_setup.jpg
    ├── DHT11_Temperature_Humidity.jpg
    ├── HC05_Bluetooth_Module.jpg
    ├── soil_moisture_sensor.jpg
    ├── water_level_sensor.jpg
    ├── relay_module.jpg
    └── mini_submersible_water_pump.jpg
```

---

# ✅ Advantages

- Automatic plant watering
- Reduces unnecessary water usage
- Reduces manual intervention
- Real-time sensor monitoring
- Bluetooth-based wireless communication
- Low-cost hardware implementation
- Easy to implement and maintain
- Machine Learning-based watering prediction
- Suitable for household plants, gardens, and small-scale irrigation

---

# ⚠️ Limitations

- Bluetooth communication has a limited operating range.
- The current system does not provide cloud-based remote monitoring.
- The Machine Learning model is trained using a synthetic dataset.
- Soil moisture readings can vary depending on soil type and sensor calibration.
- The current Arduino implementation monitors the water level but does not yet use the water-level value as a condition for pump activation.

---

# 🔮 Future Enhancements

The system can be further improved by adding:

- IoT-based remote monitoring
- Blynk or ThingSpeak integration
- Mobile application
- Cloud data storage
- Solar-powered operation
- Automatic water-level protection
- Weather-based irrigation
- Multiple plant monitoring
- Predictive irrigation scheduling
- Advanced Machine Learning models
- Remote pump control

---

# 🏁 Conclusion

The Smart Irrigation System demonstrates the integration of **embedded systems, sensors, wireless communication, and Machine Learning** to create an automated irrigation solution.

Arduino collects environmental information and automatically controls the water pump according to soil moisture conditions. The HC-05 Bluetooth module provides real-time monitoring, while the Random Forest Machine Learning model demonstrates how intelligent prediction can be incorporated into irrigation systems.

The project provides a low-cost and practical approach toward **automated and water-efficient irrigation** and can be further extended into a complete IoT-based smart farming solution.

---

# 👩‍💻 Project Information

**Project Title:** Smart Irrigation System using Arduino and Machine Learning

**Technologies:** Arduino, Embedded C/C++, Python, Machine Learning, Bluetooth

**Machine Learning Algorithm:** Random Forest Classifier

**Microcontroller:** Arduino Uno

**Communication:** HC-05 Bluetooth

**Project Type:** Academic / Embedded Systems + Machine Learning Project