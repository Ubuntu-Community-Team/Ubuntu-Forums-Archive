---
title: "Reformat to NTFS Emergency Disk Wipe"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by bill45 on 2007-12-12
Niether my Win98 boot floppy or Win98 system disk Win2K sustem disk or XP will recognize and allow me to Fdisk my Ubuntu 40GB HD sda1 ext3.

Can I FDisk and format from the Ubuntu Live CD and get the drive in condition to be readable by DOS/Win?

If not what?  I have a g4l system rescue disk with a bash prompt, is there a command I can execute from there? 

Thanks Bill

---

### Post by njparton on 2007-12-12
Download "super F disk" free off the web, burn to a CD and boot from that.

Super little program that should do all that you want.

---

### Post by The Cog on 2007-12-12
The Ubunti live CD does allow you to fdisk. It has three text based programs: fdisk, cfdisk, sfdisk and one GUI program: gparted. 

> and get the drive in condition to be readable by DOS/Win
I don't understand what you are trying to achieve though. Can you explain? Windows can't read ext3 without installing a driver (I forget the name).

Note that Linux normally likes a swap partition as well as a system partition.

---

### Post by bill45 on 2007-12-12
Thanks njparton, Cog, brilliant suggestion.  XP is installing as we speak.  Have no more time for various dead ends with Ubuntu.  I need two systems up and running.  Anyway, long story>short ... I'll try again in twenty ten. 


Bill C

---

