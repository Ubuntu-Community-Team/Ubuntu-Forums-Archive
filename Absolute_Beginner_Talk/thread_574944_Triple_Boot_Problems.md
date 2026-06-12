---
title: "Triple Boot Problems"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by fisher0065 on 2007-10-13
Ive had a dual boot system with xp/vista for a while, and want to include ubuntu into a triple boot system.  I follwed the install instructions for ubuntu, along with grub, but when I reboot, all i get is the vista bootloader.  Tried using easyBCD to add linux to the options, but gave me the error "cannot find \NST\nst_grub.mbr"  Partitions are set up as:

XP on a seperate RAID
Vista on partition one of a second hard drive
ubuntu and swap file on second and third partition of the second hard drive

Id like to just add linux to the vista bootloader, but not sure what to do.  This is my first time with a distributed linux version before, so im really lost from that side of this problem.

---

### Post by obscur156 on 2007-10-13
I have a triple boot on a single HHD.
I have used this tutorial and it worked straight forward.
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty]("http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty")

Its a dual boot tuto but i just did the same for the third boot.

XP/FEISTY/GUTSY=my triple boot .
I know nothing on multiple boot on seperate drive tought .

Best regards ,good luck budy.

---

### Post by fisher0065 on 2007-10-13
yeah, still nothing.  for some reason its creating the \NST folder on my D drive (the xp one).  since its on a totally diffrent hard drive, i didnt think it would do that.  the folder created doesnt contain the .mbr though, so it matters little.

---

### Post by kellemes on 2007-10-13
Have you tried [Super Grub Disk]("http://supergrub.forjamari.linex.org/") to fix your bootloader? Has never let me down..

---

### Post by fisher0065 on 2007-10-13
unfortunately i dont have any writeable cds to use...it says its 3.4MB, but is there some version that could fit on a floppy?  If not, im SOL

---

### Post by SpiritIsReality on 2007-10-13
howdy

any help here? hope so. maybe something about raid?
[http://www.google.ca/search?hl=en&q=site%3Ahelp.ubuntu.com%2Fcommunity+dual+boot+vista&meta=&btnG=Google+Search](http://www.google.ca/search?hl=en&q=site%3Ahelp.ubuntu.com%2Fcommunity+dual+boot+vista&meta=&btnG=Google+Search)

trails
:KS

---

### Post by obscur156 on 2007-10-13
Maybe you can use a USB KEY or USB DRIVE if you dont have cd's.?

---

### Post by fisher0065 on 2007-10-13
alright, i got it to recognise grub (i think), but when i select the linux option from the loader, it says:

Loading new partition
Bootsector from C.H. Hochstatter
Cannot load from harddisk
Insert Systemdisk and press any key

before it didnt do anything, so i assume this is a step in the right direction.

---

