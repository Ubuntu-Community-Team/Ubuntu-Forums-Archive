---
title: "Midiman Midisport 1x1 USB on PPC"
date: 2005-08-08
forum: Apple PPC Users
---

### Post by ubonetu on 2005-08-08
Does anybody have a workaround for the drivers needed to run Midisports on PPC?  My system recognizes the device:

Bus 002 Device 004: ID 0763:1010 Midiman Midisport 1x1
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 012: ID 05ac:1205 Apple Computer, Inc.
Bus 001 Device 006: ID 03f0:7004 Hewlett-Packard DeskJet 3320c
Bus 001 Device 005: ID 046d:c03d Logitech, Inc.
Bus 001 Device 004: ID 05ac:0204 Apple Computer, Inc.
Bus 001 Device 002: ID 05ac:1002 Apple Computer, Inc. Apple Extended Keyboard Hub [Mitsumi]
Bus 001 Device 001: ID 0000:0000

but I'm pretty sure I need a driver (newbie).  I found a driver package for windows but none for Apple:

[http://usb-midi-fw.sourceforge.net/](http://usb-midi-fw.sourceforge.net/)

Thanks in advance for the help,
Ubonetu

---

### Post by autocrosser on 2005-08-08
Take a look at this link---  [http://www.qbik.ch/usb/devices/showdev.php?id=1492](http://www.qbik.ch/usb/devices/showdev.php?id=1492)

Not sure if this will help, but I think it will start pointing you the way---

EDIT-- Thake a look at---  [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Midiman%2FMAudio&card=USB+Midisport+1x1.&chip=Cypress+AN2131XX&module=usb-audio](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Midiman%2FMAudio&card=USB+Midisport+1x1.&chip=Cypress+AN2131XX&module=usb-audio)

About half-way down the page--NOTE TO DEBIAN USERS--- Other than this I don't know where to go--- Luck to you!!!

---

### Post by ubonetu on 2005-08-09
Thanks, Autocrosser for the links.  After searching around all day and trying different things I found this site:

[http://ccrma.stanford.edu/planetccrma/software/nanohowtos.html](http://ccrma.stanford.edu/planetccrma/software/nanohowtos.html) 

My Midisport is now up and running and works great with rosegarden.

Gotta get some sleep...

p.s.  Everything described for i386 works on my eMac (i.e. the driver you make from a windows installer).

Okay, now...  sleep...

---

### Post by autocrosser on 2005-08-10
Glad I could lend a hand----

---

