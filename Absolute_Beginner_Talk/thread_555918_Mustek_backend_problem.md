---
title: "Mustek backend problem"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by Glugglug on 2007-09-20
Hi I need to remove all reference to the Mustek 1200 bearpaw scanner because both  xsane and kooka both see my scanner as a Bearpaw 1200 and it is a Mustek 1200 ub plus  it has worked before but only for an hour and when I tried again the next day it detected it as Bearpaw  so I know that it will work .  I uninstalled  both xsane and kooka  and then reinstalled them but that does not remove any reference to Bearpaw  .   I am very new to Ubuntu 7.04 and don't know much at all but I think  it must be the directory with the gt68xx  backend that contains  some file linked to Bearpaw  so is there any way I can delete the directory .

---

### Post by alienexplorers on 2007-09-21
See if your scanner is listed here.  This is the list of supported Mustek scanners in SANE.
> ScanExpress 1200 CP 	Parport (EPP) 	  	Good 	600x1200 dpi CIS scanner 	mustek_pp
(13) 	sane-mustek_pp
ScanExpress 1200 CP+ 	Parport (EPP) 	  	Good 	600x1200 dpi CIS scanner 	mustek_pp
(13) 	sane-mustek_pp
ScanExpress 1200 CU 	USB 	0x055f/0x0001 	Complete 	  	mustek_usb
(1.0-18) 	sane-mustek_usb
ScanExpress 1200 CU Plus 	USB 	0x055f/0x0008 	Complete 	  	mustek_usb
(1.0-18) 	sane-mustek_usb
ScanExpress 1200 FS 	SCSI 	  	Untested 	One report that it crashes the computer. SCSI driver issue? Please contact me if you own such a device. 	mustek
(1.0-138) 	sane-mustek
ScanExpress 1200 UB 	USB 	0x055f/0x0006 	Complete 	For the UB Plus, see gt68xx backend 	mustek_usb
(1.0-18) 	sane-mustek_usb
ScanExpress 1200 UB Plus 	USB 	0x05d8/0x4002 	Good 	  	gt68xx
(1.0-81) 	sane-gt68xx
ScanExpress 1200 USB 	USB 	0x055f/0x0003 	Unsupported 	Unsupported. Programming information is available. 	unsupported
(2006-06-22) 	?
ScanExpress 1200 USB Plus

---

### Post by Glugglug on 2007-09-23
Got round the problem by installing ubuntu  on half the remaining space got the backend installed no problem and scanner works . I then downloaded Gparted  live cd and deleted the first install and then resized the one that was left.

---

