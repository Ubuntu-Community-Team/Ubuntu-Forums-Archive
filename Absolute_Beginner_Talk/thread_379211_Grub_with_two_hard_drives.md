---
title: "Grub with two hard drives"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by carverj on 2007-03-08
Hi there all,
                      Below is my grub/menu.list

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
# kopt=root=UUID=4c9f901f-cfdd-45b7-8e23-29a44834c08a ro
# kopt_2_6=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

#title		Ubuntu, kernel 2.6.17-11-generic
#root		(hd1,1)
#kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro quiet splash
#initrd		/boot/initrd.img-2.6.17-11-generic
#quiet
#savedefault
#boot

#title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
#root		(hd1,1)
#kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro single
#initrd		/boot/initrd.img-2.6.17-11-generic
#boot

title		Ubuntu, kernel 2.6.17-10-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.17-10-generic (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.17-10-generic (recovery mode) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, memtest86+ (on /dev/hda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.17-10-generic (on /dev/sda2) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.17-10-generic (recovery mode) (on /dev/sda2) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, memtest86+ (on /dev/sda2) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

My question is, if you had two hard drives in your system when you installed Ubuntu, would have to edit this file in order to insert another slave drive that has data you want to retrieve?

If I try a straight switch of slave drives, it won't let me boot into anything except windows!
THanks guys

---

### Post by chewearn on 2007-03-08
Nope, menu.lst is for bootable partitions.
To retrieve data, you edit /etc/fstab to mount the new drive/partition.

---

### Post by carverj on 2007-03-08
Sorry, hehe I must be a bit ahead of myself
OK, the problem is, I have installed Ubuntu on the sda2 of my primary drive and my slave was added to the grub menu. Now I want to remove the slave in order to insert my older slave drive to gather data from it.
Only the windows boot option works from the list of partitions in grub. Any ideas why sda2 is unmountable (grub error 15 from memory ) in this senario?
Do I need to edit menu.list ?

: )

> Nope, menu.lst is for bootable partitions.
To retrieve data, you edit /etc/fstab to mount the new drive/partition.

So yeah, I'm tying to boot into sda2(Ubuntu) so that I may edit fstab and mount, etc.

---

