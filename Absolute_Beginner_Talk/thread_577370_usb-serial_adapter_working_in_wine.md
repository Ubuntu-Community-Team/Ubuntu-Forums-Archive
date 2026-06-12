---
title: "usb-serial adapter working in wine"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by zakeen on 2007-10-16
Im trying to get this sorted and Ive noticed alot of threads here asking the same question. So if anyone could please provide a step by step way of working this out, I would be very thankful ;)

---

### Post by zakeen on 2007-10-19
Maybe I need to enable just the USB port? Any ideas how to do that in wine?

---

### Post by paulphillips on 2007-10-31
See [http://www.la-sorciere.de/Wine-HOWTO/ch-serial.html](http://www.la-sorciere.de/Wine-HOWTO/ch-serial.html)

This tells you how to set up serial ports in wine.  All you need to do for USB -> Serial adaptors (assuming your kernel automatically recognises the adaptor once plugged in) is to change one of the "/dev/ttySx" entries to "/dev/ttyUSBx"

I haven't tried myself, but this is what I gather from looking around...

I plan to use this though, when I upgrade my firmware on a Digital TV HDD recorder which only supports firmware upgrades via a serial port.

Hope this helps!!

---

