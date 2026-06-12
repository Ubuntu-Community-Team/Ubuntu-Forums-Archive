---
title: "DUAL BOOT seperate 2 HDD"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by ferronica on 2007-06-23
i have total 3 HDD , ubuntu and windows loaded on seprate HDD, whenevr i want to boot my system from windows i have to change CMOS settings everytime, is there any other way without getting into CMOS  choose which HDD (OS) want to boot ?????? :( :(

---

### Post by confused57 on 2007-06-23
> **ferronica said:**
> i have total 3 HDD , ubuntu and windows loaded on seprate HDD, whenevr i want to boot my system from windows i have to change CMOS settings everytime, is there any other way without getting into CMOS  choose which HDD (OS) want to boot ?????? :( :(
You should be able to add an entry to your /boot/grub/menu.lst to boot Windows, similar to the one in this thread:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by ferronica on 2007-06-24
sorry i forgot to tell you there are 3 HDD Two SATA and One PATA , in first SATA 80 GB windows Xp Pro. installed , second SATA 200GB i use it for DATA storage only , and single PATA 40GB Ubuntu  Fiesty Fawn GNOME installed.

---

### Post by gn2 on 2007-06-24
Can you access a "Boot Device Selection Menu" by pressing F8, F2 or a similar key at boot time?

If you can just use that to select the drive to boot from.

This works if each Operating System has it's own bootloader installed on it's own drive.

---

### Post by confused57 on 2007-06-24
> **ferronica said:**
> sorry i forgot to tell you there are 3 HDD Two SATA and One PATA , in first SATA 80 GB windows Xp Pro. installed , second SATA 200GB i use it for DATA storage only , and single PATA 40GB Ubuntu  Fiesty Fawn GNOME installed.
Edit your menu.lst by opening a terminal:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

try adding these 2 entries to boot Windows to the very bottom of your menu.lst:
```
title              Windows XP test one
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

title              Windows XP test two
root               (hd2,0)
savedefault
makeactive
map                (hd0) (hd2)
map                (hd2) (hd0)
chainloader        +1
```
quit & save

you can then delete the one that doesn't work, then change the title of the one that does

Added:  If neither entry works, please post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

---

### Post by ferronica on 2007-06-24
# menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout		3

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
# kopt=root=UUID=e1443465-392f-40b5-a3b3-bdf28617915e ro

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e1443465-392f-40b5-a3b3-bdf28617915e ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e1443465-392f-40b5-a3b3-bdf28617915e ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e1443465-392f-40b5-a3b3-bdf28617915e ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e1443465-392f-40b5-a3b3-bdf28617915e ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
chainloader	+1

---

### Post by ferronica on 2007-06-24
tushar@tushar-desktop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       24321   195358401    7  HPFS/NTFS
tushar@tushar-desktop:~$

---

### Post by confused57 on 2007-06-24
You probably need the "makeactive" line in your Window's entry:
```
title              Windows XP 
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

You can see how grub recognizes your hard drive order in your device.map:
```
gedit /boot/grub/device.map
```

The above entry should work, if your device.map looks like this:
```
(hd0) /dev/sda
(hd1) /dev/sdb
(hd2) /dev/sdc
```

You might also set your bios hard drive boot order up this way also...sda, sdb, sdc, assuming sdb is your Window's hard drive.

---

