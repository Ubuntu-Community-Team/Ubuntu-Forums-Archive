---
title: "Backlight not working on MacBookPro"
date: 2016-05-03
forum: Apple Hardware Users
---

### Post by LonelyStar on 2016-05-03
Hey,

I have a macbook pro 11,1, 13'' (without nvidia card).

It worked fine with ubuntu 15.10. Then The display was replaced. I installed ubuntu 16.04 (well I started it from the usb stick), and now the backlight is not switching on.

* If I plug in an external monitor, it works fine
* The screen of the macbook pro stays black
* If I use hold flashlight onto the screen, I can see the picture. So I am assuming, that the only problem is the backlight not switching on.

I can see 2 backlight devices in /sys/class/backlight:

* acpi_video0
* intel_backlight

I tried:

* reseting the SMC using Shift-Ctrl-Alt-On/Off
* Setting the brightness via the /sys/class/backlight/* devices

Non worked.
What can I do?

Thanks!
Nathan

---

