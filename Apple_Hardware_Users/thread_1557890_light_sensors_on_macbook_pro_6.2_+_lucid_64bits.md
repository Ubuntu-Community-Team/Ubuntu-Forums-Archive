---
title: "light sensors on macbook pro 6.2 + lucid 64bits"
date: 2010-08-21
forum: Apple Hardware Users
---

### Post by Robert Biloute on 2010-08-21
Hello,



I have a macbook pro 6.2 with lucid 64 bits (installed following this: [https://help.ubuntu.com/community/MacBo … ucid#Video]("https://help.ubuntu.com/community/MacBookPro6-2/Lucid#Video"))  and I try to read the output of light sensors in order to smartly control the screen  and keyboard light.
**1st question**: It seems this functionnality did exist on previous ubuntu versions, right ?

**2nd question**: I should just have to read the 'light' file which contains the output of light sensors:
~$ cat /sys/devices/platform/applesmc.768/light
(0,0)


The trouble is this file always contains this (0,0), whatever the ambient light conditions are..



Nevertheless:


**Code:**

~$ dmesg|grep apple
[    4.496393] apple 0003:05AC:0237.0001: input,hidraw0: USB HID v1.11 Keyboard [Apple Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1a.7-1.2/input0
[    4.499260] apple 0003:05AC:0237.0002: hidraw1: USB HID v1.11 Device [Apple Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1a.7-1.2/input1
[    4.502979] apple 0003:05AC:8242.0003: hiddev96,hidraw2: USB HID v1.11 Device [Apple Computer, Inc. IR Receiver] on usb-0000:00:1d.7-1.2/input0
[    8.198273] applesmc: Apple MacBook Pro 6 detected:
[    8.198275] applesmc:  - Model with accelerometer
[    8.198277] applesmc:  - Model with light sensors and backlight
[    8.198278] applesmc:  - Model with 18 temperature sensors
[    8.199332] applesmc: device has already been initialized (0xe0, 0xf8).
[    8.199334] applesmc: device successfully initialized.
[    8.200274] applesmc: 2 fans found.
[    8.203250] input: applesmc as /devices/platform/applesmc.768/input/input10
[    8.203395] applesmc: driver successfully loaded.
[   25.056833] applesmc: light sensor data length set to 10
[   64.788156] applesmc: wait status failed: 5 != 0
[   80.741403] applesmc: wait status failed: 4 != 0
[  144.690224] applesmc: wait status failed: 5 != 1
[  224.599671] applesmc: wait status failed: 5 != 1


So it seems the system is recognizing light sensors ?

On the other hand:


**Code:**

:~$ sensors
applesmc-isa-0300
Adapter: ISA adapter
Left side  :2585 RPM  (min = 2000 RPM)
Right side :2574 RPM  (min = 2000 RPM)
TB0T:        +42.5°C                                    
TB1T:        +42.5°C                                    
TB2T:        +37.2°C                                    
TC0C:        +60.0°C                                    
TC0D:        +61.5°C                                    
TC0P:        +62.0°C                                    
TC1C:        +62.0°C                                    
TG0D:        +61.0°C                                    
TG0P:        +57.0°C                                    
TG0T:        +61.5°C                                    
TMCD:        +62.0°C                                    
TP0P:        +67.5°C                                    
TPCD:        +75.0°C                                    
Th1H:        +53.8°C                                    
Th2H:        +52.8°C                                    
Tm0P:        +70.2°C                                    
Ts0P:        +35.5°C                                    
Ts0S:        +47.2°C


here no light sensors..


I also tried:

**Code:**

~$ hal-find-by-capability --capability light-sensor --verbose
Found 0 device objects of capability 'light-sensor'


any idea ?

---

