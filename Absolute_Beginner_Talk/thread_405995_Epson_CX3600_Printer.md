---
title: "Epson CX3600 Printer"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Ahasuerus on 2007-04-10
Although a UNIX user of some thirty years' standing I am new to this distribution. So far I am VERY impressed!

I have successfully installed an Epson CX3600 printer but it's so long since I used it that some of the ink cartridges have dried up. Is there a "head cleaning" utility anywhere?

---

### Post by george29 on 2007-04-10
if you install gutenprint 5.0 

then you should have access to the following:

escputil is a command line utility which allows the user to perform a variety of maintenance tasks
on EPSON Stylus inkjet printers. These tasks include head alignment, head cleaning, nozzle check,
printer identification, and retrieval of the ink level from the printer. In order for many of the
escputil functions to work, the user must have read/write access to the raw printer device (typically
/dev/lp0, /dev/usb/lp0, and the like). On many systems, this requires superuser privileges. If
you are using packages provided by your system vendor, you may have received special instructions
about using escputil

taken from [http://gutenprint.sourceforge.net/gutenprint-users-manual.pdf](http://gutenprint.sourceforge.net/gutenprint-users-manual.pdf)

---

