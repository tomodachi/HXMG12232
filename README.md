# Notes for the LCD Display HXMG 12232-2B Rev A.

 * Im unable to find any data sheet for this particular LCD
but it seems fairly similair to other chips


* References to data for my assumptions below
raspberry gpio tutorial:   https://www.raspberrypi.org/documentation/usage/gpio/
http://geoffg.net/SG12232A_Driver.html
http://www.octagonsystems.com/Manuals/Display_CableAssemblies/LCD_4x20_4x40_Display_Cable_Manual.pdfGND


High / Low  = On/ Off in GPIO

| GND | - Ground
| VCC | - (+5V to the chip?
| V0  | - (GND to the chip?)
| RS  | - Register select signal H/L, Signal register/ Instruction input.
| NC  | - NC = no connection?
| E2  | - H: talk to micro controller 2
| NC  | - no connection
| E1  | - H: talk to micto controller 1
| RW  |  = H/L Read / Write H: chip puts already set  data in BUS. L: Allows us to place data in BUS.
| DB0 | - Databus 1-7 ( only 4 are used in 4 bit mode, can this be set on this chip?)
| DB1 |
| DB2 |
| DB3 |
| DB4 |
| DB5 |
| DB6 |
| DB7 |
| RST | - Reset probably, most datasheets with similair chips say it RST on boot.
| A = | - PWR to backlight (+5v)
| K = | - PWR to backlight (GRND)


As far as i can understand this stuff to program the LCD:

1) Set Register Select to instruction input  (otherwise is in some kind of framebuffer mode?!)
2) Set chip to talk in either 4 bit or 8 bit mode (how do we do that , or is it pre set to one of them?
3) Set which half of the display to talk to (E1 or E2)
3) Put  chip i Write mode with RW
4) Use databus to LCD layout
5) Put chip in Read mode with RW

Data sheet also reference a pin called "E"  , wich seems to be a H/L to indicate if chip is written / read from . Dont think any of the pins I have mapped are one of those


Yours truly
~tomodachi


