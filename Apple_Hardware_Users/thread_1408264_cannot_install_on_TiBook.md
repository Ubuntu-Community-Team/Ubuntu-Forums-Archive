---
title: "cannot install on TiBook"
date: 2010-02-16
forum: Apple Hardware Users
---

### Post by williamd on 2010-02-16
I tried to boot from the 9.04 Live CD on my Titanium Powerbook 550mhz. It just comes up as various grayscale lines. Very strange because i know of no problem with its ATI video. OTOH, I was able to boot the same cdrw and install onto my G4imac with no problems, even though it has nvidia graphics card.

Any ideas how to proceed in getting it to work on the TiBook? Many thanks!

-bill

---

### Post by linuxopjemac on 2010-02-16
you probably deal with a wrong Xorg.conf file.

[https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3](https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3)

[http://mac.linux.be/content/black-screen-or-missing-gui](http://mac.linux.be/content/black-screen-or-missing-gui)

[http://rockhopper.dk/old/linux/files/xorg.conf.ati128](http://rockhopper.dk/old/linux/files/xorg.conf.ati128)

---

### Post by linuxopjemac on 2010-02-16
what kind of video card is in your tibook ?

---

### Post by williamd on 2010-02-18
ATI Mobility Radeon:

  Chipset Model:	ATY,RageM6
  Type:	Display
  Bus:	AGP
  Slot:	ATI
  VRAM (Total):	16 MB
  Vendor:	ATI (0x1002)
  Device ID:	0x4c59
  Revision ID:	0x0000
  ROM Revision:	113-XXXXX-115
  Displays:
Color LCD:
  Display Type:	LCD
  Resolution:	1152 x 768
  Depth:	32-bit Color
  Built-In:	Yes
  Core Image:	Not Supported
  Main Display:	Yes
  Mirror:	Off
  Online:	Yes
  Quartz Extreme:	Supported

---

### Post by linuxopjemac on 2010-02-18
You might want to start with this one:

[http://mac.linux.be/content/xorgconf-powerbook-g4-alu-167ghz-and-external-monitor-0](http://mac.linux.be/content/xorgconf-powerbook-g4-alu-167ghz-and-external-monitor-0)

I would go for a simple alternate server installation (without X) to end with a base system which boots dine. Then try to get X working by changing Xorg.conf with the link I provide you. Then you install a desktop, like gnome or kde.

---

