---
title: "Wallstreet Powerbook, Bootx, and Ubuntu"
date: 2005-10-09
forum: Apple PPC Users
---

### Post by mross on 2005-10-09
Hello all, 

I am trying to get Ubuntu to install on my G3 Wallstreet powerbook.  This is an old world mac.  I can get it to boot off of the installation CD by using Bootx ([http://penguinppc.org/bootloaders/bootx/)](http://penguinppc.org/bootloaders/bootx/)), but it will not finish the installation.  I am using mac OS 8.6 and an HFS (not HFS+) drive partition.  I tried the pivot_root commands located at [https://wiki.ubuntu.com/Installation/OldWorldMacs](https://wiki.ubuntu.com/Installation/OldWorldMacs) but it will only mount the HFS partition as read only.  I have also tried an HFS+ partiton, and had the same problem.  Does anyone have any suggestions on getting this thing working?  Also, is there a way to use Quik to boot from open firmware without using a floppy drive (I only have a CD reader for this machine, and no other Macintosh computers to make a boot floppy from).  
I would like to get Ubuntu working on this machine, as OS 8, and 9 are rather outdated, and OSX runs rather slowly on a 233 mhz processor.

---

### Post by jdp on 2005-10-09
What are the problems you have that you needed the pivot_root stuff?  The Hoary and Breezy releases should support HFS in the install kernel.  Just do the switch to VTY2 and mount and copy w/o the pivot_root.  You are using 5.04 (Hoary) right?

Also, read: [this thread about Old-World Macs](http://ubuntuforums.org/showthread.php?t=36431)

---

### Post by mross on 2005-10-11
Ok, I gave mounting the drive and just copying the file over a shot, but the HFS partition will only mount as read only.  I even tried the -a modifer for the mount command to mount the HFS partition as read / write.  Any ideas on what could be causing this?

---

### Post by jdp on 2005-10-11
Do you have any sort of security software on the HFS partition?  At Ease, some sort of encrypter?  I don't know for sure if the install kernel isn't working.  What partitions are you working on?  Something like /dev/hda5 or hda6 for HFS probably, and hda6 or hda7 for EXT3?  When you mount, does it giver any errors?  What is the out put of **mount** after mounting the HFS partition?

---

### Post by mross on 2005-10-12
Well, I seem to have gotten it working.  I ended up switching out the hard drive for the original 2GB unit.  I guess that I just have one last question, did Apple still use a special ROM on this computer that would only work with Apple branded hard drives?  The 10GB IBM unit I have works fine in a PC laptop or with this laptop and OS 8 or 9 (but not X).

---

### Post by jdp on 2005-10-13
I'm going to venture the guess that the drive may not have had all it's blocks cleared or something if it was PC formatted before the Wallstreet.  You might try having a "Write Zeros to drive" or whatever your fav. part editor can do.  Of course there is always a **dd if=/dev/null of=/dev/hda bs=512 count=1024**, IIRC, that should wipe the first 1MB on the drive, and thus any old partition tables.  It could mess up the drive too, but YMMV. ;)

---

