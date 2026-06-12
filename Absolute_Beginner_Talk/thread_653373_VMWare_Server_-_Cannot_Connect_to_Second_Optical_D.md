---
title: "VMWare Server - Cannot Connect to Second Optical Drive"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by supersk on 2007-12-29
I'm running VMWare Server 1.04 on Ubuntu 7.10 (Gutsy).  I have one 20 GB hard drive and two optical drives (a DVD drive and a CDRW drive).  Ubuntu is installed on the entire partition of the hard drive and is able to correctly connect to both optical drives.

I then created a Windows XP guest virtual machine.  In VMWare Server, in the virtual machine settings, I set both the optical drives to "Automatically detect".  When I start the Windows XP virtual machine however, it recognizes both drives as being the DVD drive.  It doesn't see the second optical drive as being the CDRW drive.

As I mentioned before, in the Ubuntu it correctly recognizes both optical drives.  I think I may need to manually enter the location of the optical drives in VMWare for the Windows XP guest machine to see it.  In VMWare, the drop-down settings are: 

(1) Automatically Detect 
(2) /dev/hdd 
(3) /dev/hdc
(4) /dev/cdrom
(5) I also have the option of manually typing in something else as well.  

This is a noob question but how do I find out what the names of my optical drives are in Ubuntu?

---

### Post by Maxtorm on 2007-12-30
From a terminal session:```
sudo lshw
```and look for the relevant section (likely *-cdrom and similar). The logical names will be listed witth each device.

---

