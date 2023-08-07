# aSiNine_and8
Small (46.5x73.2mm) BM1397 based standalone bitcoin miner

Revision 04k, remarks:
- PWM fan: do not populate T2,JP1 & R10, unless you want to use that feature (no software support yet), replace T2 with a mosfet if you want to use it, a transistor will pull gpio9 low at startup locking the esp in programming mode.
- programming first time: some esp's will not enter programming mode automatically, in that case short gpio9 to ground at power-up (gpio9 is connected to the encircled via close to the esp32-c3). Updating the firmware is best done through OTA @ <your miner's ip address>/update)
- Powering the miner: use a 5V/3A usb charger for low power application (upto ~250GHs). If you want more powerrr use the screw terminal to connect a 9-12V power supply. I use a usb trigger (like https://www.aliexpress.com/item/1005004562492420.html) set to 9V connected to a usb charger with PD (use a high efficiency charger like https://www.aliexpress.com/item/1005004530223949.html). IMPORTANT: only connect the miner with ONE of the power inputs. Powering the miner with more than 5V and connecting it to a PC will damage the miner and the pc!!!!
- Cooling: I use a 7cm piece of https://www.aliexpress.com/item/1005001772072504.html with a 5cm 5V fan (runs on 3.3V when connected to X1) like https://www.aliexpress.com/item/1005003059434065.html strapped to the heatsink and board with tie wraps. Don't forget to use some (non-conductive!) thermal compound. This fan/heatsink combo will allow the miner to be run at upto 320GHs while staying (just) below my max asic temperature of 60C and is virtually silent.
- The firmware used is bm1397.ino.bin included in this repo, and can be used until I update & publish the source code of my firmware.
