---
title: "Can't boot to XP!"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by karlo on 2008-02-27
Before everything works correctly, probably because I resize my partition but my files are ok on my NTFS partition.

I can't boot to Windows XP...

When I seelct Windows XP from the GRUB Menu, all I can see is *Starting Windows* ...

Also is there a way to theme GRUB?

---

### Post by SunnyRabbiera on 2008-02-27
gah I hope you didnt goof up xp by mistake

---

### Post by stchman on 2008-02-27
> **karlo said:**
> Before everything works correctly, probably because I resize my partition but my files are ok on my NTFS partition.

I can't boot to Windows XP...

When I seelct Windows XP from the GRUB Menu, all I can see is *Starting Windows* ...

Also is there a way to theme GRUB?

So you resized your XP partition?  You should have done an chkdsk -f on your NFTS drives first.

---

### Post by lunar71 on 2008-02-28
you need to execute the following command and post the output:
sudo fdisk -l

and also post the contents on the menu.lst file in /boot/grub/menu.lst

---

### Post by karlo on 2008-02-28
> **lunar71 said:**
> you need to execute the following command and post the output:
sudo fdisk -l

and also post the contents on the menu.lst file in /boot/grub/menu.lst

**sudo fdisk -l**

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe233bc5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1        3705    29760381    7  HPFS/NTFS
/dev/sda3   *        6304       12161    47054385    7  HPFS/NTFS
/dev/sda4            3706        6303    20868435    5  Extended
/dev/sda5            3706        6173    19824178+  83  Linux
/dev/sda6            6174        6303     1044193+  82  Linux swap / Solaris
```

**/etc/grub/menu.lst**

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
# kopt=root=UUID=5fa0a7bf-9c05-4c58-87cd-6d20748c9334 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5fa0a7bf-9c05-4c58-87cd-6d20748c9334 ro acpi=force quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5fa0a7bf-9c05-4c58-87cd-6d20748c9334 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

---

### Post by karlo on 2008-02-28
> **stchman said:**
> So you resized your XP partition?  You should have done an chkdsk -f on your NFTS drives first.

Well, everytime I boot with XP, specially the last time, chkdsk always runs. Everything is ok, it's 100% clean of errors.

---

