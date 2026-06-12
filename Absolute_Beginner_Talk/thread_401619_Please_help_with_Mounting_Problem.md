---
title: "Please help with Mounting Problem"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by gerrymoth on 2007-04-04
Bit confused what I should be changing or naming my various drives to?
sda2 is my WinXP C: drive
sda3 is my Shared D: drive
sda5 is my Ubuntu install
sda6 is my Swap

Looking at the fdisk and fstab details below can someone give me a easy to understand step by step guide to sort things out????
:) 

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         510     4096543+  12  Compaq diagnostics
/dev/sda2   *         511        3871    26997232+   c  W95 FAT32 (LBA)
/dev/sda3            3872        5852    15912382+   c  W95 FAT32 (LBA)
/dev/sda4            5853        7296    11598930    5  Extended
/dev/sda5   *        5853        7233    11092851   83  Linux
/dev/sda6            7234        7296      506016   82  Linux swap / Solaris

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=a1d94cc5-ef28-4f83-9f6a-f4b2e3a328e5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=38c4e3c4-83de-4690-b9b1-e699fbe606c9 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by land0 on 2007-04-04
I can tell you that hda5 is the Linux partition and hda6 is the swap partition. /dev/hda2 is the XP partition abd /dev/hda3 is the shared drive. If you are trying to have the shared partition and XP partition show up automatically or "auto mounted" you will need to add them to the fstab config file. You may find step by step howto's already written for it in the forum. 

[Here is a quick link]("http://http://www.google.com/search?q=ubuntuforums%3A+mounting+windows+partitions&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a")

---

