---
title: "[SOLVED] fstab entries vs. gparted overview"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by humti-dum-ti on 2007-09-11
hello,
I'm sorry if this is some sort of silly question, but I really don't understand something in my fstab file.
This is what my fstab entry looks like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=25f9242c-30eb-4411-bb6a-108bcaa80194 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
# /dev/sda2
UUID=5e76d239-efa5-4c2b-bf3c-1455a4eee2da none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


What strikes me is that sda2 is marked as being 'swap', whereas gparted shows me the that 
sda1 is the swap drive, sda2 is marked as regular ext3 as is sda3. 

The fdisk command gives me the following:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         360     2891668+  82  Linux swap / Solaris
/dev/sda2             361        3529    25454992+  83  Linux
/dev/sda3            3530        9729    49801500   83  Linux


Another thing is that sda2 is not automounted, but that is a minor issue, I guess.

Many thanks for any advice, 

humti-dum-ti

---

### Post by overdrank on 2007-09-11
Hi here are a couple of links that may help
[http://www.comptechdoc.org/os/linux/howlinuxworks/linux_hlfilesystems.html](http://www.comptechdoc.org/os/linux/howlinuxworks/linux_hlfilesystems.html)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by steve.horsley on 2007-09-11
It may be that the comments no longer match the lines beneath. The command **blkid** will help tie things up.

---

### Post by humti-dum-ti on 2007-09-12
Thx for the blkid command. I found out that my entries re UUID don't match with the actual UUID's. After making my system unbootable for a while I figured it out (the swap partition wasn't even activated...) and it seems to be working fine now.
Thx a lot again!

---

