---
title: "After repositioning partitions, dual-booting has become impossible..."
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by Starks on 2007-12-16
If I install Ubuntu, Vista will bluescreen on start up... If I restore the MBR, I can't restore GRUB or boot Ubuntu.

Please help!

---

### Post by forestpixie on 2007-12-16
can you post these - 

```
cat /etc/fstab
cat /boot/grub/menu.lst
sudo fdisk -l
```

---

### Post by Starks on 2007-12-16
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=5a586540-ad02-44e3-81d4-73e4d2f995e8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=196a1bef-6317-4506-945f-67332e9d4f15 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
eric@kingfisher:~$ cat /boot/grub/menu.lst
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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# kopt=root=UUID=5a586540-ad02-44e3-81d4-73e4d2f995e8 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5a586540-ad02-44e3-81d4-73e4d2f995e8 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5a586540-ad02-44e3-81d4-73e4d2f995e8 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)

---

### Post by Starks on 2007-12-16
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17061   137042451    7  HPFS/NTFS
/dev/sda2           17062       19351    18394425   83  Linux
/dev/sda3           19352       19457      851445    5  Extended
/dev/sda5           19352       19457      851413+  82  Linux swap / Solaris

Disk /dev/sdb: 512 MB, 512483328 bytes
255 heads, 63 sectors/track, 62 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000884db

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          62      497983+   6  FAT16

---

### Post by Starks on 2007-12-16
Please help.

---

### Post by MangasColoradas on 2007-12-16
Would re-installing Grub from the install disk work?

---

### Post by torgrot on 2007-12-16
I think you need to add these to lines to your menu.lst at the end of the windows entry
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root (hd0,0)
makeactive
chainloader	+1

torgrot

---

### Post by Starks on 2007-12-16
> **MangasColoradas said:**
> Would re-installing Grub from the install disk work?

It's not a GRUB problem.

---

### Post by Starks on 2007-12-18
It's still not working...

---

### Post by abicash on 2007-12-18
Hi 
Why dont you use the SUPERGRUB disk?
It was a great help to me,and I could correct either GRUB errors or NTDLR (windows boot) errors.Just google for it

---

### Post by Starks on 2007-12-18
> **abicash said:**
> Hi 
Why dont you use the SUPERGRUB disk?
It was a great help to me,and I could correct either GRUB errors or NTDLR (windows boot) errors.Just google for it

I have been using it. IT DOESN'T FIX THE PROBLEM.

---

### Post by forestpixie on 2007-12-18
the title says you can't dual boot - and you can't restore the MBR - what problem do you get then that means you can't restore grub

- but you haven't actually told us what the problem is 

can you not boot ubuntu or vista?

what about togrot's post - did you try that?

it would probably help if you told us what you've actually tried to do to help.

and don't shout

---

