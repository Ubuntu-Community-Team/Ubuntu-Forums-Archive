---
title: "Printer drivers don't work with AMD64?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by blazini on 2007-07-26
I'm trying to get this Epson all in one scanner/printer working. I found the drivers and I tried installing from source, /configure seems to work without errors, but "make"  and "makeinstal"l return errors like "make: *** [install-recursive] Error 1".

The only RPM I could find is for i386 and it turns up errors somewhere in the middle that AMD64 not supported.

Any ideas?

---

### Post by ReaderRat on 2007-07-26
What kind of printer (Model#) is it?

---

### Post by blazini on 2007-07-26
Epson Stylus CX6000 it's an all in one printer scanner copier. I have the drivers, they just don't install on my system. 

I found extra backend files for Xsane on Symantec, but they didn't do much good.

---

### Post by ReaderRat on 2007-07-27
What system do you have, 32- or 64-bit??

Your specific printer is not listed in the printer database, but some CX6x00 are. You might want to browse [[color=blue]THIS[/color]](http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX6300) 
Where did you find your driver? I didn't find one for linux on the Epson website.

---

### Post by blazini on 2007-07-27
Sure it is [http://openprinting.org/show_printer.cgi?recnum=Epson-stylus_CX6000]("http://openprinting.org/show_printer.cgi?recnum=Epson-stylus_CX6000")
down toward the bottom, not where it should be. It's an AMD64 pc, I can see the printer in system/administrator/printing, but it doesn't recognize it. There is no option for USB port. Adding it like this (through CUPS) shouldn't need a seperate driver, but like I said, it doesn't work

The driver packages I have came from here [http://www.avasys.jp/english/linux_e/dl_spc.html]("http://www.avasys.jp/english/linux_e/dl_spc.html")

---

