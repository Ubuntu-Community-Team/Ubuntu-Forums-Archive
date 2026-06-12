---
title: "Grub Hangs: &quot;Starting Up ...  GRUB&quot;"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by opalsky on 2007-08-14
ON IDE0 i have XP which doesnt boot since Grub, and on IDE1 I have feisty which boots fine.

I have tried XP Cd boot and  fixmbr without success.  I have tried the map (hd0) (hd1) etc option without success, but this is only for XP not on the 1st drive anyway.

/ and /boot are located on  /dev/hdc4 
already tried  [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

In fstab, both XP and Xubuntu partitions have the same UUID, is this wrong? Are some old mappings from a previous map (hd0)... operation creating confusion?

If I cannot get XP back I would at least like to access IDE0 from Xubuntu

Thanks in advance

(As background, I successfully had dualboot running, with the remove XP drive physically and plug it back in method, hence GRUB was on IDE1 drive, I had to reinstall Xubuntu and accidentally now it is on IDE0 as well, and booting frojm IDE0 Grub)


results of fdisk -l 

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14945   120045681    7  HPFS/NTFS

Disk /dev/hdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        9727    78132096    7  HPFS/NTFS
/dev/hdc2            9728       18238    68364607+  83  Linux
/dev/hdc3           19742       19929     1510110    5  Extended
/dev/hdc4           18239       19741    12072847+  83  Linux
/dev/hdc5           19742       19929     1510078+  82  Linux swap / Solaris


I noticed IDE drive 0 and 1 have same UUID in fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc4
UUID=2f1dc739-82e6-425e-99d9-0e3fba8f728a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc2
UUID=9730eef6-f052-4f81-980a-56dd78fa6c2b /home           ext3    defaults        0       2
# /dev/hda1
UUID=80C2F69090FA0800 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc1
UUID=80C2F69090FA0800 /media/hdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc5
UUID=ee537fbb-719d-4b9d-8178-262ad2b60f2b none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0




now for menu.lst


## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2f1dc739-82e6-425e-99d9-0e3fba8f728a ro

# groot=(hd1,3)


title        Ubuntu, kernel 2.6.20-16-generic
root        (hd1,3)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=2f1dc739-82e6-425e-99d9-0e3fba8f728a ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root        (hd1,3)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=2f1dc739-82e6-425e-99d9-0e3fba8f728a ro single
initrd        /boot/initrd.img-2.6.20-16-generic


title        Ubuntu, memtest86+
root        (hd1,3)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows
rootnoverify (hd0,0)
makeactive
chainloader +1

---

### Post by opalsky on 2007-08-14
I discovered I needed to run

FIXBOOT

and

FIXMBR

on the IDE0 XP partition to fix the master boot record (FIXMBR alone insufficient!)

then I unplugged IDE0, and installed Grub back on the IDE1, note that the BIOS numbering is now opposite to the menu.lst numbers (because IDE0 was unplugged when grub installed, so grub thinks IDE1 is hd0)

then the map (hd0) (hd1) etc for the XP section

---

