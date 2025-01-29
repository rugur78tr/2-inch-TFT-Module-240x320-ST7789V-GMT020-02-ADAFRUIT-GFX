# 2-inch-TFT-Module-240x320-ST7789V-GMT020-02-ADAFRUIT-GFX
How to run a 2 inch TFT Module 240x320 ST7789V GMT020-02 on ESP8266(Nodemcu) with Adafruit GFX and ST7789 Libraries



## Connections;

VCC to 3.3V

GND to GND

SCL to D5 (GPIO 14)

SDA to D7 (GPIO 13)

RES to D2 (GPIO 4)

DC to D1 (GPIO 5)

CS to D3 (GPIO 0)


#include <Adafruit_GFX.h>       // Core graphics library
#include <Adafruit_ST7789.h>    // Hardware-specific library for ST7789
#include <SPI.h>                // SPI library

// Define the pins used for the display
#define TFT_CS        0   // Chip select pin (D3)
#define TFT_RST       4   // Reset pin (D2)
#define TFT_DC        5   // Data/Command pin (D1)

// Initialize the display
Adafruit_ST7789 tft = Adafruit_ST7789(TFT_CS, TFT_DC, TFT_RST);

void setup() {
  // Initialize serial communication for debugging
  Serial.begin(115200);
  Serial.println("Initializing display...");

  // Initialize the display
  tft.init(240, 320); // Initialize the display with size 240x320
  
  // Set rotation (optional, can be 0, 1, 2, or 3)
  tft.setRotation(1);
  
  // Clear the screen with a black color
  tft.fillScreen(ST77XX_BLACK);

  // Confirm initialization
  Serial.println("Display initialized");

  // Draw some graphics
  tft.setTextColor(ST77XX_WHITE);
  tft.setTextSize(2);
  tft.setCursor(10, 10);
  tft.print("Hello, World!");

  tft.drawCircle(120, 160, 50, ST77XX_RED);
  tft.fillRect(50, 200, 140, 60, ST77XX_BLUE);

  // Confirm drawing
  Serial.println("Graphics drawn");
}

void loop() {
  // Nothing to do here
}
