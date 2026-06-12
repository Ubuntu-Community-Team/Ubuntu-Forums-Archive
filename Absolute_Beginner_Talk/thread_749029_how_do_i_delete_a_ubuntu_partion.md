---
title: "how do i delete a ubuntu partion?"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by catroaring on 2008-04-08
running 7.10

i installed and broke the UI, so i installed again(which works).  the broke install still shows up in the BIOS.  how do i delete it?

---

### Post by Cannaregio on 2008-04-08
In the BIOS?
You mean in grub?
If so, just edit grub:

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by warp99 on 2008-04-08
> **catroaring said:**
> running 7.10

i installed and broke the UI, so i installed again(which works).  the broke install still shows up in the BIOS.  how do i delete it?

What do you mean you "broke" the UI. You can purge and reinstall some or all of the desktop components if you need to, there's no need to reinstall the entire operating system. Linux is a module operating system, so you can do this very easy.

---

### Post by catroaring on 2008-04-08
yes grub not BIOS.  im still a noobie with linux.  this is what i get from gksudo gedit /boot/grub/menu.lst

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
# kopt=root=UUID=5c906fe2-4de4-4c79-99d9-92480da08698 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5c906fe2-4de4-4c79-99d9-92480da08698 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5c906fe2-4de4-4c79-99d9-92480da08698 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5c906fe2-4de4-4c79-99d9-92480da08698 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5c906fe2-4de4-4c79-99d9-92480da08698 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.20-16-generic (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2bcdc22a-870f-4e81-9bf6-43e307cd7453 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2bcdc22a-870f-4e81-9bf6-43e307cd7453 ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2bcdc22a-870f-4e81-9bf6-43e307cd7453 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2bcdc22a-870f-4e81-9bf6-43e307cd7453 ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, memtest86+ (on /dev/hda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


what do i delete?

---

### Post by warp99 on 2008-04-08
Simple, just delete these entries:

```
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title Ubuntu, kernel 2.6.20-16-generic (on /dev/hda1)
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=2bcdc22a-870f-4e81-9bf6-43e307cd7453 ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/hda1)
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=2bcdc22a-870f-4e81-9bf6-43e307cd7453 ro single
initrd /boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title Ubuntu, kernel 2.6.20-15-generic (on /dev/hda1)
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=2bcdc22a-870f-4e81-9bf6-43e307cd7453 ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/hda1)
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=2bcdc22a-870f-4e81-9bf6-43e307cd7453 ro single
initrd /boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title Ubuntu, memtest86+ (on /dev/hda1)
root (hd0,0)
kernel /boot/memtest86+.bin
savedefault
boot

```

That's what the header file is telling you: 

> This entry automatically added by the Debian installer for an existing linux installation on /dev/hda1

So if you delete the entries you only delete the boot entries, not that actual partition. To do that you would need to run 'sudo fdisk /dev/hda' to remove it from the partition table.

---

