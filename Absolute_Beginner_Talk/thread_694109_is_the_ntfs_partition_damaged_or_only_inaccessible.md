---
title: "is the ntfs partition damaged or only inaccessible because of mbr?"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by luvinit on 2008-02-11
On dual boot one drive system the WIndows XP partition is not recognized at boot. Gparted says it is there, it can be mounted but not read. 

here are some outputs of commands:

~$ sudo fdisk -l

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         446     3582463+  83  Linux
/dev/hda2             447        1175     5855692+  83  Linux
/dev/hda3            1176        2026     6835657+  83  Linux
/dev/hda4            2027        2434     3277260   82  Linux swap / Solaris

this says that hda1 is linux not, ntfs

grub can't seem to repair the boot setup

grub> root (hd0,0)
 Filesystem type unknown, partition type 0x83

grub> setup (hd0)

Error 17: Cannot mount selected partition

do you think this is an mbr problem only or that the NTFS partition is damaged? 

Thanks

---

### Post by pytheas22 on 2008-02-11
try booting to a live CD and trying to boot to your first partition from there.  I think the command for that is something like "grub reboot 1"  That should tell you whether the issue is your MBR or not.

You could also try running chkdsk on the Windows partition from the XP installation disk, or try using badblocks to analyze it (I'm not sure if that will work with ntfs, however).  testdisk, available in the repositories I think or on a lot of recovery Linux live CDs, might also be useful to check for partition corruption.

---

### Post by luvinit on 2008-02-11
thanks a lot, I will try those suggestions.  I tried the pclinux Os livecd because that does a lot of things such a automounting of partitions, but it couldn't do it.

---

