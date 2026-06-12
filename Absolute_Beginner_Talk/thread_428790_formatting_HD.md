---
title: "formatting HD"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by fast eddie on 2007-04-30
I want to partition my second hard drive to FAT32 so I can access it using Ubuntu or Windows XP on what will soon be a dual boot machine.

However, when I right click on the drive and then click on format it is only giving the NTFS file system as an option. How do I format this drive to be FAT32?

cheers

---

### Post by oilchangeguy on 2007-04-30
probably the easiest way is if you have a win 98 boot floppy, if not go to [www.bootdisk.com](www.bootdisk.com) and create one. then using only that drive (set to master) boot from the floppy. at the a>: type fdisk, and follow the prompts and delete whatever partition is on the drive now. then create a new partition and reboot, get to an a>: prompt and type format c:  this will format the drive to fat 32. if you don't have a floppy from the link you can probably burn it to a cd.

---

### Post by bobbybobington on 2007-04-30
A lot of other distros (non-livecd) have a program called cfdisk (which is awesome for formatting and partions) included in their installer. I use the vector linux one, but only for cfdisk, not for installing:) .

---

