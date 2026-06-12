---
title: "Printing trouble with HP laserjet 4P"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by General Disarray on 2007-09-09
I have spent the last 10 hours attempting to print to my HP laserjet 4P. When I started today, the printer was Shared on my Win XP desktop. Win machines connected to the network could print, but I could not print from Ubuntu. (This machine printed fine until I changed to Ubuntu) I thought it was just intentional incompatibility by M$oft to make using Linux harder. I thought I would outsmart them. I built a dedicated Linux print server out of an old 486/66. It works. I can print all day from the XP box, but not the Ubuntu box.

The CUPS web interface has this to say:
Make and Model: HP LaserJet 4P Foomatic/hpijs (recommended)
Printer State: idle, accepting jobs, not published. 
Device URI: ipp://192.168.1.252:9100 

I have tried all driver/ setting combinations I can think of. When I “print” a test page, the print spool says ”Printing:job-printing” along with a print job number to mock me with the number of failed test pages. (most common) Sometimes it says “Job complete” (rare) Sometimes it says “Stopped:job-stopped” (says that one a lot too) Always: No Test Page! The Ready light on the printer blinks when it says “Job complete” as if it is receiving data, but stops blinking before printing would normally start.

I would include some usr/bin/etc/hda/crap/ in there, but I just don't know any. I just hate M$soft and am trying to find an alternative to Vi$ta that can also use printers.

---

### Post by kevstar31 on 2007-09-15
did you try gutenprint?
first you need to get glutenprint with synaptic then use the
[ppd here.]("http://http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_4P")

---

### Post by Daveth on 2007-09-15
or the stuff on here

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_4P](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_4P)

---

