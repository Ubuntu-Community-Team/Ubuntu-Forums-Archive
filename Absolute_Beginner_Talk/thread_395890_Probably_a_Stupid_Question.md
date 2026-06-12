---
title: "Probably a Stupid Question"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by J11Gyro on 2007-03-28
Was browsing thru Symatec package manager programs and updates and found a version for my XP2400,Linux kernel image for version 2.6.15 on AMD K7 SMP/UP. Should I download and install?
I am running linux-image-2.6.15-28-386 right now and everything is fine except I am not sure the problems with Wine and VMware are not caused by lack of support for my CPU to a extent.

---

### Post by yabbadabbadont on 2007-03-28
The package you would install would be linux-k7.  That will pull in all the needed packages for an AMD K7 processor.  After it is installed, you will have to reboot.  Choose the K7 entry at the grub boot screen.  I very much doubt that it will help with your WINE and VMWare problems though.

---

### Post by J11Gyro on 2007-03-28
Very good advice, not sure why but it won't boot to that version anyway hhmmmm. I mean I am kinda way ahead of the 386 version when it comes to hardware, wonder why it will not run the K-7 version

---

### Post by igknighted on 2007-03-28
Do you have any proprietary drivers installed, especially the NVIDIA ones?  If so, they have modules that are built for the old kernel and wont work with the K7 one.  You need to reinstall the driver so it installs the module for your new kernel.

---

