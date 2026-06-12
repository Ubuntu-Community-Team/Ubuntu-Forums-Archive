---
title: "dedicated mac pro 3,1 ubuntu install?"
date: 2009-02-21
forum: Apple Hardware Users
---

### Post by babag on 2009-02-21
all of the postings and info i've turned up in searches regarding
linux, debian, or ubuntu on a mac pro seem to assume osx is 
installed. when trying out new things, i like to thoroughly 
separate my stable system from my testing system by removing the 
stable drive and using a clean drive in its place. that assures me
that i won't accidentally do something bad to my stable drive's 
contents - the entire system.

i'm interested in trying out ubuntu studio as well as 64studio. in
looking into these i've found a lot of discussion about efi, mbr, 
and graphics cards but the assumption in discussing installation is 
always that osx is in the system and refit and bootcamp are 
possibly in use.

what do i do in my scenario, though? i will have a clean system
with no existing partitions or operating systems. can ubuntu be
installed on a mac pro in this scenario? is there a guide anywhere
as to how to do this?

just for laughs, i tried the latest 8.10 64bit install disk. it
began the install ok but reached a point where the screen blanked 
and that was it. had to do a hard reset and remove the drive and
go back to my osx system.

would love to try these things but at a loss as to how to proceed.
pointers welcome.

thanks,
BabaG
(system specs follow)

Hardware Overview:

  Model Name:	Mac Pro
  Model Identifier:	MacPro3,1
  Processor Name:	Quad-Core Intel Xeon
  Processor Speed:	2.8 GHz
  Number Of Processors:	2
  Total Number Of Cores:	8
  L2 Cache (per processor):	12 MB
  Memory:	2 GB
  Bus Speed:	1.6 GHz
  Boot ROM Version:	MP31.006C.B05
  SMC Version:	1.25f4

PIONEER DVD-RW  DVR-112D:

  Model:	PIONEER DVD-RW  DVR-112D
  Revision:	BC14
  Detachable Drive:	No
  Protocol:	ATAPI
  Unit Number:	0
  Socket Type:	Internal
  Low Power Polling:	Yes

ATI Radeon HD 2600 XT:

  Chipset Model:	ATI Radeon HD 2600
  Type:	Display
  Bus:	PCIe
  Slot:	Slot-1
  PCIe Lane Width:	x16
  VRAM (Total):	256 MB
  Vendor:	ATI (0x1002)
  Device ID:	0x9588
  Revision ID:	0x0000
  ROM Revision:	113-B1480A-252
  EFI Driver Version:	01.00.252
  Displays:
Hanns.G HG281:
  Resolution:	1920 x 1200 @ 60 Hz
  Depth:	32-bit Color
  Core Image:	Hardware Accelerated
  Mirror:	Off
  Online:	Yes
  Quartz Extreme:	Supported
  Rotation:	Supported
  Television:	Yes
Display:
  Resolution:	3840 x 1024 @ 60 Hz
  Depth:	32-bit Color
  Core Image:	Hardware Accelerated
  Main Display:	Yes
  Mirror:	Off
  Online:	Yes
  Quartz Extreme:	Supported
  Rotation:	Supported

---

### Post by cyberdork33 on 2009-02-22
It sounds like you are taking the right approach. You will very likely need to burn a refit cd in order to sync the partition tables properly after installing.

I don't know what the problem is with your installer hangup. You might try the alternative install cd.

"Installation" is pretty much the same for any mac. Check out the Apple Intel Installation wiki:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

Once you get the system installed and working, you can probably put both drives in your mac, install refit and choose to boot between them. You will run into the multiple hard drive oddity that occurs though:
[http://wiki.debian.org/DebianOnIntelMacPro#line-187](http://wiki.debian.org/DebianOnIntelMacPro#line-187)

---

