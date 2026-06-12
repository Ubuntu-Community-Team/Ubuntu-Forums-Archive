---
title: "Canon i900D"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by AlanD on 2007-03-18
Has anyone gotten a Canon i900D to work under Ubuntu? It's not a model listed in the printers section and the generic printer doesn't work. Ubuntu sees the printer and even identifies it as a Canon i900d, but I can't get the damn thing to print - there are no error messages. Any suggestions would be appreciated.

---

### Post by Madpilot on 2007-03-19
There isn't a "Canon i900D" listed at all in the Linuxprinting [database]("http://openprinting.org/printer_list.cgi"). Odd, and it makes it that much harder to actually help you with the thing.

Have you tried googling "Canon i900D Linux" or similar?

---

### Post by ramjet_1953 on 2007-03-19
Canon are notorious for their lack of Linux support.

However, as a last resort, you could try TurboPrint. [http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

It is not free, but you can dowload a working demo, to make sure it will suit.

It is not expensive and a whole lot cheaper than buying a new printer.

Regards,
Roger :cool:

---

### Post by AlanD on 2007-03-21
Under recommendation of another post i cannot find anymore, I tried the BJC-7000 driver and it works beautifully now. Thanks for the quick replies :)

---

### Post by AlanD on 2007-03-21
Ok cancel that, it now compresses everything to the top left 8th of the page.. switching to high quality printing driver fixes that but the text is horridly jaggy and ugly :<

---

### Post by Maxtorm on 2007-06-22
I know this thread is a little stale, but just in case any one else is trying to print to an i900D:

I used the BJC-7000 drivers under 7.04 and was able to print without issue (no qualities problems as noted by the poster above).  I selected the BJC-7000 and then chose "High Quality Image (simple)" from the Driver list.

---

### Post by morphball on 2007-11-18
Just another addition (yes, there is still no proper driver over 1 year after the last post, but Vista doesn't support it at all...); the i900D prints fine in 7.10 (even over smb to a 2K/XP share) using the "Canon BJC-7000 - CUPS+Gutenprint v5.0.1 Simplified" driver. To fix the problem with the driver only printing to half the page, go to the "Printer Options" under the Printer configuration, and select "1200x600 DPI" under Resolution.

---

### Post by SupraBlur on 2008-01-19
I've followed these instructions for my i900D and it seems to be printing fine, but I noticed there's no advanced control over the print quality like there was in Windows, and also no reporting of my ink cartridge level.  Any fixes for these?

-Ray

---

