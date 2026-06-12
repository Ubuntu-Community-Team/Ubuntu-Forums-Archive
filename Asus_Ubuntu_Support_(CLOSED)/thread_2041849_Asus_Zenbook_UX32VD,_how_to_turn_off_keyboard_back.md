---
title: "Asus Zenbook UX32VD, how to turn off keyboard backlight and adjust brightness?"
date: 2012-08-13
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Linuxpal on 2012-08-13
I'm having a battery issue. When my battery is fully charged, i only got 2:30 hours before it's empty again... Asus says battery should hold 4-5 hours under normal use, but I only get as said 2:30 hours. Anyway, since I got such a crappy battery I need to somehow "make" it use less power. I can't be bothered returning the laptop, because I've upgraded both RAM and to SSD.

How can I turn off backlight for keyboard (fn+f2 does not work in ubuntu)

How can I adjust screen brightness, is there any program you recommend?

All this is to reduce power use, if anyone know about something else i should try to reduce the use of power, please tell me :)

---

### Post by ActionpackedPIVII on 2012-08-13
Here is some instructions I followed to enable brightness controll when using nvidia-current driver: 
.All you need to do is:

  **sudo gedit /etc/X11/xorg.conf   find segment like this:**
 Section "Device"
Identifier    "Default Device"
Driver    "nvidia"
Option    "NoLogo"    "True"
EndSection  

change it to:

 Section "Device"
Identifier    "Default Device"
Driver    "nvidia"
Option    "NoLogo"    "True"
Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection

  Then restart,It will work.
 

I don't know anything about the keyboard backlight, but as they are problably small leds, I don't believe they take up too much battery.

However a great way to say battery, is by using Jupiter.

Jupiter is an easy way to handle CPU profiles (such as powersafe, performance, on-demand)
read more about jupiter here:
[http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html#more-13276](http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html#more-13276)

---

### Post by semiosis on 2013-01-10
On quantal at least you can run this command to turn off the keyboard backlight...

echo 0 | sudo tee /sys/class/leds/asus::kbd_backlight/brightness

See also: [https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)

---

