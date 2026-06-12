---
title: "adding printer driver?????"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by tty23 on 2006-12-11
I clicked on system > administration > printing, clicked on New Printer, detected my printer, selected my my manufacturer, model, and driver, clicked install driver....Here is where I'm having problems, Im told to "Select a PPD File", I dont know what that is, where they are or anything else. This is my first time using linux of course

---

### Post by Sef on 2006-12-11
What's your make and model of printer?

> clicked on New Printer, detected my printer, selected my my manufacturer, model, and driver, clicked install driver.

Click foward instead of install driver.

---

### Post by tty23 on 2006-12-11
lexmark, 3000, pcl3

---

### Post by tty23 on 2006-12-11
i skipped install driver... and clicked forward, tried to print but nothing happened, also after install will the scanner work, its a all in one model

---

### Post by Tzumli_D on 2006-12-11
This is the blind leading the blind, but my 2 cents worth ( I have a current query regarding printer set up in this forum)
There is a lot of information in the various tutorials and information, just not altogether in one place.
.ppd files are associated with post script printers, and your printer, if it is a ps printer will either work better or needs the .ppd file [I don't know as I'm a fairly new linux user too]
Have a look in the file browser, under etc at the cups folder. If the .ppd folder is there you are at the same stage as me.
Denise

---

### Post by Sef on 2006-12-11
Read [LinuxPrinting]("http://linuxprinting.org/show_printer.cgi?recnum=Lexmark-3000"). 

Lexmark is not well supported since they keep their drivers proprietary.

---

