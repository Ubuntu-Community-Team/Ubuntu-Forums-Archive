---
title: "How do I install my HP scanner?"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by lentomies on 2007-11-26
Hello,

 I have a HP Scanjet 3300c scanner and I would like to install it in Ubuntu 7.10 but don't know how.

If someone could guide me I'd be most appreciative.

Thank you.....

---

### Post by linuxwizard on 2007-11-26
look over these should get you going
[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

[http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD](http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD)

---

### Post by alienexplorers on 2007-11-26
Heres a list of supported scanners according to sane:
```
Manufacturer: Hewlett-Packard

Link(s): http://www.hp.com, http://www.hp.com/
Model 	Interface 	USB id 	Status 	Comment 	Backend 	Manpage
Photo Scanner 1000 	USB 	0x03f0/0x1001 	Unsupported 	Not supported by SANE. However, it's detected as mass storage device so just mounting it is reported to work. See link for device data. 	unsupported
(2006-06-22) 	?
Photosmart 1200 Photo 	USB 	  	Unsupported 	Probably not supported by SANE. No details known. 10x15 cm. Maybe similar to Photo Scanner 1000? 	unsupported
(2006-06-22) 	?
PhotoSmart PhotoScanner 	SCSI 	  	Complete 	  	hp
(1.06) 	sane-hp
Photosmart S20 (C5101A) 	USB 	0x03f0/0x0102 	Unsupported 	Not supported yet by SANE. See link for details. 	unsupported
(2006-06-22) 	?
Photosmart S20xi (C7150A) 	USB 	0x03f0/0x0102 	Unsupported 	Not supported yet by SANE. See link for details. 	unsupported
(2006-06-22) 	?
ScanJet 3c 	SCSI 	  	Complete 	  	hp
(1.06) 	sane-hp
ScanJet 3p 	SCSI 	  	Complete 	  	hp
(1.06) 	sane-hp
ScanJet 4c 	SCSI 	  	Complete 	  	hp
(1.06) 	sane-hp
ScanJet 4p 	SCSI 	  	Complete 	  	hp
(1.06) 	sane-hp
ScanJet 5p 	SCSI 	  	Complete 	  	hp
(1.06) 	sane-hp
ScanJet 5s 	Parport (EPP) 	  	Minimal 	Requires libieee1284 library. Only gray mode. 	hpsj5s
(0.03) 	sane-hpsj5s
ScanJet 2100C 	USB 	0x03f0/0x0505 	Complete 	  	plustek
(0.51) 	sane-plustek
ScanJet 2200C 	USB 	0x03f0/0x0605 	Complete 	  	plustek
(0.51) 	sane-plustek
ScanJet 2300C 	USB 	0x03f0/0x0901 	Complete 	600x1200 dpi max 	genesys
(1.0-8) 	sane-genesys
ScanJet 2400c 	USB 	0x03f0/0x0a01 	Unsupported 	GL646 based, to be added to genesys backend 	unsupported
(2006-06-22) 	?
Scanjet 3200C 	Parport (EPP/ECP) 	  	Good 	works (relabelled 1220P and 2000P) 	umax_pp
(1) 	sane-umax_pp
ScanJet 3300c 	USB 	0x03f0/0x0205 	Complete 	  	niash
(0.3) 	sane-niash
ScanJet 3400c 	USB 	0x03f0/0x0405 	Complete 	If you use Linux 2.6, version 2.6.8 or newer is necessary. 	niash
(0.3) 	sane-niash
ScanJet 3500C 	USB 	0x03f0/0x2205 	Good 	  	hp3500
(1.0, NEW!) 	sane-hp3500
ScanJet 3530C 	USB 	0x03f0/0x2005 	Good 	  	hp3500
(1.0, NEW!) 	sane-hp3500
ScanJet 3570C 	USB 	0x03f0/0x2005 	Good 	  	hp3500
(1.0, NEW!) 	sane-hp3500
ScanJet 3670c 	USB 	0x03f0/0x1405 	Unsupported 	GL646 based, to be added to genesys backend 	unsupported
(2006-06-22) 	?
ScanJet 3690c 	USB 	0x03f0/0x1405 	Unsupported 	GL646 based, to be added to genesys backend 	unsupported
(2006-06-22) 	?
ScanJet 3770 	USB 	0x03f0/0x2505 	Unsupported 	While an external binary-only backend exists, it works only on Linux i386. Therefore the scanner is unsupported on other platforms. 	unsupported
(2006-06-22) 	?
ScanJet 3800c 	USB 	0x03f0/0x2605 	Unsupported 	Probably unsupported, see link for details. 	unsupported
(2006-06-22) 	?
ScanJet 4100C 	USB 	0x03f0/0x0101 	Complete 	  	hp
(1.06) 	sane-hp
ScanJet 4200C 	USB 	0x03f0/0x0105 	Basic 	8bpp color, 75/150/300/600 dpi only 	hp4200
(1.0-2) 	sane-hp4200
ScanJet 4200Cse 	USB 	0x03f0/0x0105 	Basic 	8bpp color, 75/150/300/600 dpi only 	hp4200
(1.0-2) 	sane-hp4200
ScanJet 4200Cxi 	USB 	0x03f0/0x0105 	Basic 	8bpp color, 75/150/300/600 dpi only 	hp4200
(1.0-2) 	sane-hp4200
ScanJet 4300c 	USB 	0x03f0/0x0305 	Complete 	If you use Linux 2.6, version 2.6.8 or newer is necessary. 	niash
(0.3) 	sane-niash
ScanJet 4300c/Silitek 	USB 	0x047b/0x1002 	Complete 	If you use Linux 2.6, version 2.6.8 or newer is necessary. 	niash
(0.3) 	sane-niash
ScanJet 4500C 	USB 	0x03f0/0x1205 	Unsupported 	Maybe GL841_HP, but not confirmed, maybe can be added to genesys backend 	unsupported
(2006-06-22) 	?
ScanJet 4570C 	USB 	0x03f0/0x1305 	Unsupported 	Maybe GL841_HP, but not confirmed, maybe can be added to genesys backend 	unsupported
(2006-06-22) 	?
ScanJet 4600 	USB 	0x03f0/0x3005 	Unsupported 	Not supported. See link for details. 	unsupported
(2006-06-22) 	?
ScanJet 4670 	USB 	0x03f0/0x3005 	Unsupported 	Not supported. See link for details. 	unsupported
(2006-06-22) 	?
ScanJet 4850C 	USB 	0x03f0/0x1b05 	Unsupported 	GL841, maybe can be added to genesys backend 	unsupported
(2006-06-22) 	?
ScanJet 4890C 	USB 	0x03f0/0x1b05 	Unsupported 	GL843, maybe can be added to genesys backend 	unsupported
(2006-06-22) 	?
ScanJet 5100C 	Parport 	  	Complete 	Requires ppscsi driver and epst module 	hp
(1.06) 	sane-hp
ScanJet 5200C 	Parport USB 	0x03f0/0x0401 	Complete 	Parallel interface requires ppscsi driver and epst module 	hp
(1.06) 	sane-hp
ScanJet 5300C 	USB 	0x03f0/0x0701 	Complete 	1 pass, 2400 dpi - regularly tested - some FW revisions have x-axis image scaling problems over 1200 dpi 	avision
(Build: 201) 	sane-avision
ScanJet 5370C 	USB 	0x03f0/0x0701 	Good 	1 pass, 2400 dpi - some FW revisions have x-axis image scaling problems over 1200 dpi 	avision
(Build: 201) 	sane-avision
ScanJet 5400c 	USB 	0x03f0/0x1005 	Basic 	  	hp5400
(1.0-2) 	sane-hp5400
ScanJet 5470c 	USB 	0x03f0/0x1105 	Basic 	  	hp5400
(1.0-2) 	sane-hp5400
ScanJet 5490c 	USB 	  	Basic 	  	hp5400
(1.0-2) 	sane-hp5400
ScanJet 5500C 	USB 	0x03f0/0x1305 	Unsupported 	Maybe GL841_HP, but not confirmed, maybe can be added to genesys backend 	unsupported
(2006-06-22) 	?
ScanJet 5530C Photosmart 	USB 	0x03f0/0x1605 	Unsupported 	Maybe GL841_HP, but not confirmed, maybe can be added to genesys backend 	unsupported
(2006-06-22) 	?
ScanJet 5550C 	USB 	0x03f0/0x1205 	Unsupported 	Maybe GL841_HP, but not confirmed, maybe can be added to genesys backend 	unsupported
(2006-06-22) 	?
ScanJet 5590 	USB 	0x03f0/0x1705 	Unsupported 	Not supported. See link for details. 	unsupported
(2006-06-22) 	?
ScanJet 6100C 	SCSI 	  	Complete 	  	hp
(1.06) 	sane-hp
ScanJet 6200C 	SCSI USB 	0x03f0/0x0201 	Complete 	  	hp
(1.06) 	sane-hp
ScanJet 6250C 	SCSI USB 	0x03f0/0x0201 	Complete 	  	hp
(1.06) 	sane-hp
ScanJet 6300C 	SCSI USB 	0x03f0/0x0601 	Complete 	  	hp
(1.06) 	sane-hp
ScanJet 6350C 	SCSI USB 	0x03f0/0x0601 	Complete 	  	hp
(1.06) 	sane-hp
ScanJet 6390C 	SCSI USB 	0x03f0/0x0601 	Complete 	  	hp
(1.06) 	sane-hp
ScanJet 7400c 	USB 	0x03f0/0x0801 	Good 	1 pass, 2400 dpi - dual USB/SCSI interface 	avision
(Build: 201) 	sane-avision
ScanJet 7450c 	USB 	0x03f0/0x0801 	Good 	1 pass, 2400 dpi - dual USB/SCSI interface - regularly tested 	avision
(Build: 201) 	sane-avision
ScanJet 7490c 	USB 	0x03f0/0x0801 	Good 	1 pass, 1200 dpi - dual USB/SCSI interface 	avision
(Build: 201) 	sane-avision
ScanJet 7650 	USB 	0x03f0/0x1805 	Unsupported 	Not supported. See link for details. 	unsupported
(2006-06-22) 	?
ScanJet 8200 	USB 	0x03f0/0x0b01 	Good 	1 pass, 4800 (?) dpi - USB 2.0 	avision
(Build: 201) 	sane-avision
ScanJet 8250 	USB 	0x03f0/0x0b01 	Good 	1 pass, 4800 (?) dpi - USB 2.0 	avision
(Build: 201) 	sane-avision
ScanJet 8290 	USB 	0x03f0/0x0b01 	Good 	1 pass, 4800 (?) dpi - USB 2.0 and SCSI - only SCSI tested so far 	avision
(Build: 201) 	sane-avision
ScanJet IIc 	SCSI 	  	Complete 	  	hp
(1.06) 	sane-hp
ScanJet IIcx 	SCSI 	  	Complete 	  	hp
(1.06) 	sane-hp
ScanJet IIp 	SCSI 	  	Complete 	  	hp
(1.06) 	sane-hp
ScanJet Plus 	Propietary 	  	Complete 	Driver for HP parallel interface card required 	hp
(1.06) 	sane-hp

```

---

### Post by HermanAB on 2007-11-26
Basically you install Sane and then you just plug the scanner in.  It should work instantly all by itself.  Sane stands for: Scanner Access Now Easy.  Basically, someone got very annoyed at the problem and fixed Linux scanning really well.

---

### Post by magicfab on 2008-04-03
Hi,

I have that scanner (HP 5590) which I hadn't used for about 3 years (when I got rid of the last Windows machine I had around). I was about to sell it this week and decided to plug it in 7.10 and 8.04.

Long story short it works perfectly. In 7.10 nothing happens when turning it on, I have to start xsane. In 8.04 xsane starts automatically. In both cases it's detected and working just fine. Nothing special is required, just start xsane in Applications > Graphics.

Xsane is the default scanning application, I didn't install anything specific or addition in either 7.10 or 8.04 (beta).

---

