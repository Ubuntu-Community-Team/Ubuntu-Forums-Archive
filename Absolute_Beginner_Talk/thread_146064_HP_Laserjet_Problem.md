---
title: "HP Laserjet Problem"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by _simon_ on 2006-03-17
For every page I print I also get a blank plage.

I printed a 49 page document the other day and at the end it fed through 49 blank pages.

What can I do to prevent this?

Printer: HP Laserjet 4+ on LPT1
Driver: ljet4
This is a local printer.

---

### Post by _simon_ on 2006-03-18
Does anyone have any ideas?

---

### Post by chuckyp on 2006-03-18
Try a different printer driver.  I noticed my hp I have to pick the vague deskjet series for it to function properly rather than the actual model number.

---

### Post by Bagnaj97 on 2006-03-18
I havent got that printer so I can't help. Maybe this page can help though. [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_4_Plus](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_4_Plus). You could try using the custom PPD from that page (when you install the printer there's a bit somewhere that says install driver).

---

### Post by _simon_ on 2006-03-19
Thanks a lot mate, that has solved my problem!

Much appreciated :)

---

### Post by ivarf on 2006-05-05
I have the same problem with 8 Ubuntu 5.10 machines connected to a Laserjet 4 plus. The printer has 2 MB memory and is connected to the network through HP Jetdirect. This printer has no postscript, so for me PCL is the only option. I have tried the hpijs, lj4dith and ljet 4 drivers. I have used the hpijs driver for some time now as it gives the best print results. The only problem is that It prints a blank page after every job.

I have tried to reduce the printers resolution from 600 dpi to 300 dpi. After I did that it prints no more blank pages when printing tests from the printer setup. But it still prints a blank pages when printing from other applications like Firefox. Perhaps a memoryupgrade of the printer would fix the problem? If I do an upgrade I will let you know

I use A4-pages in the printer and have chosen A4 as the default paper-size.

---

