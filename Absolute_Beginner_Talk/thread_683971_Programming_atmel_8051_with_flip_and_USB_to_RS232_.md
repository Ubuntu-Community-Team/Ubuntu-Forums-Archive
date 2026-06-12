---
title: "Programming atmel 8051 with flip and USB to RS232 converter"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by fb2007 on 2008-01-31
I'm trying to use atmel flip (to program 8051 uc) with ATEN UC-RS232A usb to serial converter. With 'dmesg' i see that aten usb2rs232 is connected to /dev/ttyUSB0. But when I start Flip I can only use /dev/ttyS*. Can somebody help me?

---

### Post by krlhc8 on 2008-04-02
I am currently having the same problem but with pl2303 driver USB-Serial device.  In another thread, Tormod explains how to create a rules script to automatically create a /dev/ttyS4 link when you plug in your /dev/USB0 device.  Here's the link:
[http://ubuntuforums.org/showthread.php?t=322759&page=3](http://ubuntuforums.org/showthread.php?t=322759&page=3)

I tried this with Flip, and I still got a time-out error.  I'm not sure what to do either... :(

---

### Post by Coso on 2008-05-07
I am having the same problem with pl2303. Contacted Atmel support. They promised to release a new FLIP version that would take care of it. However, they announced it for early March... I checked back with them (3 weeks ago) and they say it is coming any day now. So have a look at their website. In the meantime I am compiling with sdcc under Linux, but do the FLIP loading under Windows (URGGR).

---

