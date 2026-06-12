---
title: "Running a Wacom Bamboo under Ubuntu"
date: 2011-12-16
forum: Art &amp; Design
---

### Post by theKuch on 2011-12-16
I bought a Wacom Bamboo .

I did a search for programs that can operate this and found, and installed, MyPaint.

However, the device does not respond. (It worked fine in Gates & Doors :-( )

Do I need to install a driver? Where do I find such a beast?

Thanks

---

### Post by ofnuts on 2011-12-16
> **theKuch said:**
> I bought a Wacom Bamboo .

I did a search for programs that can operate this and found, and installed, MyPaint.

However, the device does not respond. (It worked fine in Gates & Doors :-( )

Do I need to install a driver? Where do I find such a beast?

Thanks
Everything is there: 

[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page)

---

### Post by Favux on 2011-12-16
Hi theKuch,

It depends on what model Bamboo and what release of Ubuntu you are using.  For example a new third generation Bamboo Pen and Touch requires you to update your wacom.ko (the usb kernel driver/module) to the one from input-wacom-0.12.0.  However that will only work for Natty and Oneiric.  See the instructions on the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

The model is on the back of the tablet on one of the labels.  You can get the product ID from entering:
```
lsusb
```
in a terminal.

---

### Post by theKuch on 2011-12-19
I have the CTH-470  :-(

---

### Post by Marzata on 2011-12-19
Xubuntu 11.10 and Wacom Bamboo MTE-450 work like a charm in MyPaint 0.9.1. Thank you all in the community!

---

### Post by Favux on 2011-12-19
Hi theKuch,

The CTH-470 (Product ID = 0xde) or the Bamboo Capture is new this October.  So that model is not yet in the default usb kernel driver/module or in the X driver xf86-input-wacom even in Oneiric.  But support for it has been added upstream so all you need to do is follow the instructions on the [Bamboo PT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") part I. and part II and install input-wacom-0.12.0 and clone xf86-input-wacom-0.12.0.  But you do have to be using Natty (kernel 2.6.38 ) or later.


Hi Marzata,

Sounding good!  :)

---

