---
title: "Grub error, with details"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by mindwip on 2007-04-21
Hello all.  Some quick back round. I installed Ubuntu on a new hard drive i just added today (hard drive 4). I already had XP on hard drive one. When i finished installing Ubuntu, it booted right into windows. So i figured why dont i reinstall Ubuntu agian this time i moved the drive to my first Sata slot. Unpluged  all my other drives. Install went just fine. Then i added the rest of the drive. Ubuntu saw them all fine. So i have tried to add XP to the Grub and it is not working.
Here are my current settings. when i select xp to boot up. It says, "starting up" and hangs there no error message. I am waiting for about 7 secs then i give up is that too soon? Also are my settings right. Xp is installed on the first partion  on sdd ? 


I know the Xp is fine and can boot no problem be fore Ubuntu.

Thanks


Oh even thou my Ubuntu is installed on sata one Ubuntu thinks its sdc1

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         857     6883821   83  Linux
/dev/sda2            1688       38914   299013624    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3             858        1687     6666975   83  Linux
/dev/sda5            1688       19547   143448448+   7  HPFS/NTFS
/dev/sda6           19547       38914   155565112+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12160    97675168+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60044   482303398+  83  Linux
/dev/sdc2           60045       60801     6080602+   5  Extended
/dev/sdc5           60045       60801     6080571   82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       13578   109060528+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdd2           13578      119522   850995205   72  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdd3           45382       79243   271987362   74  Unknown
Partition 3 does not end on cylinder boundary.





>  # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=099e6ac4-1387-4c21-b10f-b7b1adbef689 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=099e6ac4-1387-4c21-b10f-b7b1adbef689 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=099e6ac4-1387-4c21-b10f-b7b1adbef689 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title Microsoft Windows XP
root (hd3,0)
savedefault
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by mindwip on 2007-04-21
OK i fixed it, 


I have a program called super grub disk. Its boot able and can boot windows or a linux, i ran it and tried to boot from the disk  xp was on it worked, when i told it windows was on second drive. Once it worked, i did it again and used the pause break key to see what it did.

title Microsoft Windows XP
!!!!map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
chainloader +1
boot!!!


the wording inbetween !!! was how it booted the drive. I coped that over to the grub in Ubuntu. Problems solved. Hope this helps some one else one day. If some one has th esame problem as me copy this 


title Microsoft Windows XP
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
chainloader +1
boot


To get your xp to boot on a second drive. Cheers

---

