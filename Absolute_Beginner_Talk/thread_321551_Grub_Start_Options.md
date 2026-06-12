---
title: "Grub Start Options"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by John E on 2006-12-19
Every so often, my installation of Ubuntu (6.06) starts refusing to boot. It stops at the section saying "Mounting the root partition". It won't continue, either in normal mode or recovery mode. If I wait for a long enough time, it eventually displays a message about being unable to mount /dev/hdc6

I've looked in **fstab** which contains no references to /dev/hdc6. Also, there aren't any references in **menu.lst**. However, **menu.lst** contains this strange section referring, not to hdc6 but to hdc1, hdc2 and hdc7:-

```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hdc7 ro
```

I don't need to boot from /dev/hdc1 or /dev/hdc2 or /dev/hdc7 (and never have done) so can I safely eliminate this section? Also, are there any other files I should check to see where this mysterious /dev/hdc6 is coming from?

---

### Post by useResa on 2006-12-19
I can not answer the question on how this got into your menu.lst

However, all lines that you have posted are only comments (because they start with #). 
So none of these are actually used when you start. 

 Therefor, you could remove them but it will not change anything.
 You could test this by making a back-up copy (always a smart thing to do when you alter such important files) of this file, remove the lines and restart.

---

### Post by John E on 2006-12-19
Hi there. I've found out a bit more information. If I try to boot up in normal mode I eventually get this message:-

**ALERT! /dev/hdc7 does not exist. Dropping to a shell**

whereas, in Recovery mode I get this, which is slightly different:-

**ALERT! /dev/hdc6 does not exist. Dropping to a shell**

Does anyone know where these messages might be coming from?

---

### Post by Bachstelze on 2006-12-19
Could you please paste the entire /boot/grub/menu.lst as well as /etc/fstab and the ouput of *sudo fdisk -l* ?

---

### Post by John E on 2006-12-19
Thanks for the help - this is **menu.lst**:-

```
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
default		5

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=/dev/hdc7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Windows XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

and this is** fstab**:-

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext2    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

and here's the output from **fdisk -l**:-

```
Disk /dev/hda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1721    13823901    c  W95 FAT32 (LBA)
/dev/hda2            1722        3442    13823932+   c  W95 FAT32 (LBA)
/dev/hda3            5164       14596    75770572+   f  W95 Ext'd (LBA)
/dev/hda5            5164        5294     1052226   82  Linux swap / Solaris
/dev/hda6            5295        7015    13823901   83  Linux
/dev/hda7            7016        8736    13823901    b  W95 FAT32
/dev/hda8            8737       14596    47070418+   b  W95 FAT32
omitting empty partition (5)

Disk /dev/hdc: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        1721    13823901   1c  Hidden W95 FAT32 (LBA)
/dev/hdc2            1722        3442    13823932+  1c  Hidden W95 FAT32 (LBA)
/dev/hdc4            5164       20023   119362950    f  W95 Ext'd (LBA)
/dev/hdc5            7016        8736    13823901    b  W95 FAT32
/dev/hdc6            8737       14596    47070418+   b  W95 FAT32
```

---

