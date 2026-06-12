---
title: "[SOLVED] Grub Error 15"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-12-11
I don't know what question to ask, now. Grub has "failed", I guess.

grub> geometry (hd0)
drive 0x80: C/H/S = 38913/255/63, The number of sectors = 625142448, /dev/sda
Partition num: 0, Filesystem type is ext2fs, partition type 0x83
Partition num: 1, Filesystem type unknown, partition type 0x82
Partition num: 2, Filesystem type is ext2fs, partition type 0x83
Partition num: 3, Filesystem type is ext2fs, partition type 0x83

grub> root (hd0,0)

grub> setup (hd0)
Checking if "/boot/grub/stage1" exists... no
Checking if "/grub/stage1" exists... no

Error 15: File not found

and:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1 36607 294045727 83 Linux
/dev/sda2 38393 38647 2048287+ 82 Linux swap / Solaris
/dev/sda3 * 38648 38913 2136645 83 Linux
/dev/sda4 36608 38392 14338012+ 83 Linux

I've looked at the Grub Error Collection at Gentoo's:

[http://www.gentoo.org/doc/en/grub-error-guide.xml?style=printable](http://www.gentoo.org/doc/en/grub-error-guide.xml?style=printable)

I've tried the SuperGRUB LiveCD, but it reports an Error 15 as well. 


HOW can I fix this?

---

### Post by aun on 2007-12-12
It appears that when you run "Setup", the program is not finding either of two files:

/boot/grub/stage1     or
/grub/stage1

There are two possible reasons I can think of.  Either these files really don't exist, or you are looking in the wrong place (partition or directory).  I haven't had to run any setup for grub before, but I'm not sure yet if you need to.  Here are some of the questions I would ask to get started in the right direction:

I take it grub was working correctly before?

Have you done any changes to your BIOS lately?  In particular, changing boot order?

Have you made any changes to the menu.1st file?

Have you made any other significant changes, like installing a new distro, just prior to this occurring?

I see three "Linux" partitions.  What are they?  Do you have more than one distro installed?

Were you working from a LIve CD when you ran setup?

---

### Post by Mark_in_Hollywood on 2007-12-12
This was a non-recoverable error. Gutsy has been re-installed.

---

