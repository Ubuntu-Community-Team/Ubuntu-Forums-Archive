---
title: "hardware RAID5"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by rdelgar on 2007-08-26
Has anyone used a hardware RAID5 card sucesfully with Ubuntu?
What model RAID card has Ubuntu support?

Robert

---

### Post by wirelessmonkey on 2007-08-26
Please don't post multiple threads with the same topic... I answered this in your other thread.

---

### Post by kevdog on 2007-08-26
3-ware makes cards with linux drivers, and releases the source so you can compile also.  I have one of those dang cards around here somewhere but I havent used it with linux yet (in Windows its awesome!!).  Their technical support is excellent and they have a 3 year warranty -- RMA'd my last card at 2 years 11 months because something wasnt working -- no questions asked.

---

### Post by cdenning on 2007-10-09
Does anyone have a package for NVidia RAID5 (hardware) support for Ubuntu?  I am trying not to have to use WinJunk Vista but my HTPC has to have RAID5 for my data.  Vista even has the drives built in that actually work.

Setup:

MB - KFN32-D SLI (nVIDIA MCP55 nForce Professional 3050 I/O companion chip and Intel® 6702PXH 64-bit PCI Hub)
Dual AMD Opteron 2214 Processors
Dual Boot - Vista and Ubuntu hopefully (AMD 64bit)

I feel like I am running naked without RAID5.  Please help me get away from Billy boys junk OS. He has bite me to many times to go back.

---

### Post by wirelessmonkey on 2007-10-09
If you can see your drives in linux, then you can RAID5 them using mdadm.

---

### Post by cdenning on 2007-10-09
Correct me if I am wrong but mdadm is a software RAID package.  I need to use dmraid but it appears that it does not to support RAID5.  Does anyone have a fix/workaround or package for this capability. Can a driver even be purchased?  ASUS has them for RedHat only and I have a request into them to build a Ubuntu package.

I even tried to install the Beta for Ubunty 7.10 and it is still broke in it.  Looks like WinJunk will have to continue for this HTPC/Repository?  I hope not...

---

