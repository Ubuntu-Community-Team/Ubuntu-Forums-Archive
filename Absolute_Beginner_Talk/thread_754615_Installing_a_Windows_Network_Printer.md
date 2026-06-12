---
title: "Installing a Windows Network Printer"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by drbk563 on 2008-04-14
How do I install a network printer which is shared by a windows xp system? The printer is a Xerox Phaser 3400. I do not believe this printer is supported by linux.

Thank You

---

### Post by Squish on 2008-04-14
Well, if you can, go with HP next time for a linux printer.
Other than that, I personally would search the specific model in google, and write ubuntu at the end. Theres bound to be a tread with it,

Good luck!

---

### Post by joshrobinson on 2008-04-14
youll want to make sure the printer is shared on the windows machine

install samba ```
apt-get install samba
```
set it up so you are on the same workgroup

then go to system > administration > printing

click new printer, go to windows printer via samba
click browse, browse to the windows pc, and click the printer

youll have to find a driver that works, it goes by model
when all said and done, try to print a test page

---

### Post by drbk563 on 2008-04-14
Thank for all your help. Next time I will get an HP printer.

---

