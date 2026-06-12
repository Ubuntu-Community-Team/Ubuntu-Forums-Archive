---
title: "USB2.0 Issue with External HDD"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Leviathan05 on 2007-08-10
I have used a Comstar 320GB external HD in WIndows for over 5 months and never had an issue.  I have since switch to Ubuntu, and still want to use this drive.  However, I am having some "sketchy" problems with it.  Each time I try to copy any number of files over to the drive, it will lock solid, and eventually lock up the entire system.

It worked fine in Windows.

The motherboard is a Gigabyte GA-7N400-L, with 4 USB ports that are all USB2.0.  However, the only way I have managed to get it working consistently in Ubutnu (7.0.4) has been to go in to the machine BIOS and change the USB specifications from 1.1/2.0 to just 1.1.  The drive does not lock up at all.  I have even made sure that I am using a USB2.0 certified cable with it.

Any ideas?  I do not want to use 1.1.... the transfer rates suck.  I'd really hate to go back to Windows on this.

---

### Post by GMachine_24 on 2007-08-11
Hi:

To avoid reinventing the wheel, you might want to check out this thread.

[http://ubuntuforums.org/showthread.php?t=506623](http://ubuntuforums.org/showthread.php?t=506623)


Good luck.

gm

---

### Post by Leviathan05 on 2007-08-11
Thanks for the reply on this.  However, the issue I have is not dependent on the format of the drive (NTFS.EXT3, FAT32).  It is seems to be that the USB 2.0 drivers that are being used just do not work properly.  As stated, I have run this drive in Windows XP with blazing speeds.  However, with Ubuntu, I have to drop to 1.1 to get it to work.

---

