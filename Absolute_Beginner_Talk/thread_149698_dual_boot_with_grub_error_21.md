---
title: "dual boot with grub error 21"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by flyingsolo on 2006-03-24
Need help with dual boot on Dell box (P4/2.4GHz/512 RAM) which has WXPHE on Master hard drive (160GB) and I just installed a 2nd 200GB Seagate IDE drive (slave) to put Linux on it.  The install seemed to go smoothly with the usual Ubuntu setup but when it finally asks you to remove the install CD and it does a reboot, I got the message: 
Loading stage 1.5,
Loading please wait.
r21

which apparently indicates a Grub error 21.  Haven't found any explanation as to what that indicates or how to fix.  Much obliged for help or links to prior posts re same.

---

### Post by flyingsolo on 2006-03-24
Update--surprise, surprise I fixed it myself!  (wonders never cease)
A little do-diligence came up with the following post:

[http://linuxfromscratch.org/pipermail/lfs-support/2005-March/026477.html](http://linuxfromscratch.org/pipermail/lfs-support/2005-March/026477.html)

where I discovered the BIOS had not recognized the existence of the 2nd drive (was labelled as "OFF"; switched to "AUTO") and now all is well with dual boot on two separate drives.

---

### Post by az on 2006-03-24
Grub 21 means that your bios does not see the hard drives in the same way that the linux kernel does.

Since Grub runs before the linux kernel is loaded into memory, it has to use the information from BIOS.  Sometimes, the bios is buggy and gives wrong information.  Sometimes it may invert the drive order -  something you can address by editing the device.map file in the /boot/grub directory.  You can also try playing around with bios settings to see if you can change the ide drive mode for the disk(s).

You can usually work around this problem.  If you don't have the live cd, you can use theinstaller to boot your system and edit the files from the command line.

---

### Post by az on 2006-03-24
There you go!

w00t!

You rock and I type too fast....

---

