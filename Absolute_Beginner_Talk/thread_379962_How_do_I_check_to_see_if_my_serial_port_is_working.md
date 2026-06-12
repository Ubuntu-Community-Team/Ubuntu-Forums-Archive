---
title: "How do I check to see if my serial port is working?"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2007-03-09
I've tried installing two different printers (HP 2P and Brother 1440) and neither is being detected. They are indeed older printers, but still, I think the odds are rather slim that neither is detectable. Thanks in advance.

---

### Post by troymcdavis on 2007-04-04
Won't it show up System -> Administration -> Device Manager?

---

### Post by woooee on 2007-04-05
There is such a thing as a serial port printer, but they are old and rare.  If it is a parallel port printer you can test it with
ls /etc/fstab | lpr
If it prints then the printer is recognized and you probably haven't set up CUPS correctly.

---

