---
title: "adding windows on raid 0 to grub"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by mooglinux on 2007-08-01
Hello all, i have finally made the switch to linux, and so far am fairly happy aside from a few problems. In particular is dual-boot. I have ubuntu, the bootloader and swapspace on a 10gig hdd, set to ide master. ide slave is my dvd drive, and my windows installation is on a raid 0 configuration of 2 80gig hdd's, and the raid is done via the nvidia chipset, NF4 SLI.

here is what fdisk has to say:

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       20022   160826683+   7  HPFS/NTFS

Disk /dev/hda: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1188     9542578+  83  Linux
/dev/hda2            1189        1247      473917+   5  Extended
/dev/hda5            1189        1247      473886   82  Linux swap / Solaris


perhaps i read this incorrectly, but it looks as tho liux sees the two individual drives in the raid, rather than the single partition they form.  i have tried editing menu.lst several ways, and it looks like this:


title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=33d93f55-44c7-455e-858d-1c2791d53793 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Windows XP Professional
root		(hd1,0)
makeactive
chainloader	+1

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=33d93f55-44c7-455e-858d-1c2791d53793 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=33d93f55-44c7-455e-858d-1c2791d53793 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=33d93f55-44c7-455e-858d-1c2791d53793 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(sdb1)
kernel		/boot/memtest86+.bin
quiet


i have tried setting root for windows to (hd1,0) it will get so far as to say "starting" but windows never appears. But setting it to (sdb1), (sdb1,0), (sdb0,0), (sdb0) and many other such settings, has cause it to spit out error 23. What is my problem and what do i need to do?

---

