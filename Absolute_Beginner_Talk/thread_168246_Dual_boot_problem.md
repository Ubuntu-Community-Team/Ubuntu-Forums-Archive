---
title: "Dual boot problem"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by infoseeker on 2006-04-30
I have installed Ubuntu onto a second harddisk (hdc) with Windows on the primary (hda).
I removed the Windows drive completely during the installation and have been doing CMOS changes (drive boot order) each time I need to change back to Windows.
I am having problems with grub detecting the Windows partition for some reason :confused: 
menu.lst entry:
> # This entry automatically added by the Debian installer for a non-linux OS
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
chainloader	+1
boot
I know the (hd1,0) section is correct as I can detect the partions if I attempt to edit this entry on bootup, but the error I always get is
> Partition num:0, Filesystem type unknown, partition type 0x7
It is NTFS formatted.  Is it normal that hda1 becomes (hd1,0) if I change the boot order in this way and has this got something to do with the problem ?

Thanks

---

### Post by dave9191 on 2006-04-30
From what i remember grub starts counting your drives from 0 rather then 1. So if you have windows installed on the first partion on the first drive it should be hd(0,0).

--
Dave

---

### Post by infoseeker on 2006-04-30
Thanks for the reply Dave.

Just did a double check and if I enter (within grub) grub > root (hd0,   (then tab for auto-completion), my hdc (ext3) partitions are listed.

Thanks anyway.

---

### Post by syg00 on 2006-04-30
Xp needs to boot from the BIOS primary drive; use the following to fool it```
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
``` (replace your root line)

---

### Post by infoseeker on 2006-04-30
Thanks...will try that.

EDIT : That sorted it out, thanks :D

> rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)

---

