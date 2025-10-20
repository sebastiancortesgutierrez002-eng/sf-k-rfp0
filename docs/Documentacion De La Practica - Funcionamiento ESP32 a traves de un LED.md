# 📚 Documentacion De La Practica - Funcionamiento ESP32 a traves de un LED

---

# 1) Resumen

- ## **Nombre del proyecto:** Oscilador Astable con 555
- ## **Autor:**  Sebastián Cortes
- ## **Curso / Asignatura:** Introduccion a la mecatronica 
- ## **Fecha:** 05/09/2025  
- ## **Descripción breve**: El Objetivo de la clase fue explorar las bases del funcionamiento de un microcontrolador ESP-32, enfocado hacia la programacion en ARDUINO para demonstrar el potencial del microcontrolador con un LED
# -----------------------------------

# 2) Objetivos

## **General:** Comenzar con las bases de la programacion en arduino y lograr conectar jumpers XY de manera correcta para el uso del ESP-32
## **Específicos:** 
## - Diseñar el circuito con valores adecuados de resistencias y capacitores.
## - Calcular teóricamente los tiempos alto y bajo de la señal.
## - Verificar en la práctica el correcto parpadeo del LED.
## - Comparar resultados teóricos y experimentales.

# -----------------------------------

# 3) Alcance y Exclusiones

## **Incluye:**
### Implementación de tres programas independientes cargados a la ESP32.
### Manera de Conexion y Uso a traves de Bluetooth
### Uso del LED en GPIO 2 y botón en GPIO 4.
### Código para todos los ejercicios.

## - **No incluye:** 
### - Diseño de PCB.

# -----------------------------------

# 4) Requisitos

## **Hardware**
### 1 × Placa de programacion tipo ESP32
### 1 × LED 
### 1 × Resistencia limitadora (220 Ω)
### 1 × Botón (pulsador)
### 1 × Resistencia Pull-down (10 kΩ)
### 1 × Protoboard y jumpers
### Fuente de alimentación de 5 VDC
### Telefono Celular (ANDROID) con Bluetooth y aplicación Bluetooth

## **Conocimientos previos**
### - Programacion Basica
### - Ley de Ohm y cálculo de resistencias
### - Uso de protoboard y multímetro

# -----------------------------------

# 5) Instalación

## Montaje del protoboard:
### Conectar el LED al GPIO 32 y el Botón al GPIO 33 
### Cargar cada uno de los tres códigos de forma individual a la ESP32 para verificar su funcionamiento.

## Pruebas :

### Etapa 1: Verificar el parpadeo de 1 s.
### Etapa 2: Verificar el encendido solo al presionar el botón.
### Etapa 3: Emparejar por Bluetooth y enviar comandos HIGH / LOW.

## Codigos para realizar Pruebas:

# ///////////////////////////////////
## 1er Codigo - BLINK 

### // Definición del pin del LED const int ledPin = 32; // 
### void setup() { pinMode(ledPin, OUTPUT); }
### void loop() { // Enciende el LED digitalWrite(ledPin, HIGH); delay(1000); // Espera 1 segundo
### // Apaga el LED digitalWrite(ledPin, LOW); delay(1000); // Espera 1 segundo }
# ///////////////////////////////////

# ///////////////////////////////////
## 2ndo Codigo - PULSADOR

### // Definición de pines const int ledPin = 33; // LED en GPIO 2 const int buttonPin = 4; // 

### void setup() { pinMode(ledPin, OUTPUT); // El botón está conectado con una resistencia pull-down externa pinMode(buttonPin, INPUT); }

### void loop() { // Leer el estado del botón (HIGH al presionar) int buttonState = digitalRead(buttonPin);

### // Escribir el estado del botón directamente al LED digitalWrite(ledPin, buttonState);

### delay(0); // }
# ///////////////////////////////////

# ///////////////////////////////////
## 3er Codigo - Control Bluetooth a traves de telefono celular

### BluetoothSerial SerialBT; const int ledPin = 2; String message = ""; // 

### void setup() { Serial.begin(115200); pinMode(ledPin, OUTPUT);

### SerialBT.begin("ESP32_Control_LED"); // Nombre del dispositivo BT Serial.println("Bluetooth iniciado."); }

### void loop() { if (SerialBT.available()) { char incomingChar = SerialBT.read();


### if (incomingChar != '\n') {
### message += incomingChar;
### } else {
### message.trim();
### message.toUpperCase();

###  Serial.print("Comando recibido: ");
###  Serial.println(message);

###  if (message == "HIGH") {
###    digitalWrite(ledPin, HIGH);
###    SerialBT.println(" LED ON");
###  } else if (message == "LOW") {
###    digitalWrite(ledPin, LOW);
###    SerialBT.println(" LED OFF");
###  } else {
###    SerialBT.println(" Comando inválido. Use HIGH o LOW.");
###  }
# ///////////////////////////////////

# 6) Resultados

## Practicos: 
### 1. Parpadeo del LED
### 2. Pulsador funcional
### 3. Conexion Bluetooth 

## Personales:
### Logre comprender las bases de la programacion utilizando ARDUINO, de igual manera me ayudo a entender como un microcontrolador puede ser muy util al momento de realizar un proyecto

