---
title: "grub error 15"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by ispy on 2008-01-20
Last night I deleted all my partitions except for my Ubuntu one, then moved that to the left to make it first, and made two new partitions and a linux swap partition (in that order). now, when I try to boot up, Grub tells me "Error 15, please wait" and hangs up. What does this mean and what can I do about it? I'm trying to learn as much as possible about linux, so If somebody could explain exactly what this means and help me fix it, that would be awesome.

thanks

---

### Post by frup on 2008-01-20
Grub is looking for your old partitions and your main one doesn't even exist to grub.

there is /boot/grub/menu.lst which you need to edit to fix the problem. This can be done from a liveCD.

> 
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4872a23b-ff95-44fa-a297-553e2001f284 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic


do you notice the (hd0,0) bit? Yours is likely different to what it is meant to be hd0,0 means drive 1 partition 1 in grub speak. Your old root may have been hd0,1 and is now hd0,0 or something like that. You may also have other entries which are not needed if you were dual booting and removed any other installed systems.

If you need more help a good way to start is by posting the contents of menu.lst. Remember, use a LiveCD and on the liveCD look at the partition you had ubuntu installed for /boot/grub/menu.lst not the liveCD's files :)

---

### Post by ispy on 2008-01-20
So if I only have Ubuntu now, will I just need to delete everything that is uncommented in GRUB and just enter the code you gave me?

I notice there is also a recovery option for Ubuntu and a memtest+86 or something...

do I need those?

---

### Post by ispy on 2008-01-20
Sorry, here's my menu.list

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
timeout		20

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
splashimage=(hd0,2)/boot/grub/splashimages/mac08.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=310c5326-e442-4d25-af54-62b7cb6935b3 ro

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
# defoptions=quiet splash locale=en_US

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=310c5326-e442-4d25-af54-62b7cb6935b3 ro quiet splash locale=en_US
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=310c5326-e442-4d25-af54-62b7cb6935b3 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows NT/2000/XP
root		(hd0,3)
savedefault
makeactive
chainloader	+1

title Puppy Linux 300 frugal
rootnoverify (hd0,2)
kernel /puppy300/vmlinuz pmedia=satahd psubdir=puppy300
initrd /puppy300/initrd.gz


```

the first entries i see are actually Kubuntu, but for some reason were titled Ubuntu. then I had Ubuntu, windows, and Puppy. I'm not sure if I still have Puppy, but windows and Kubuntu are gone. I didn't need them.

---

### Post by ispy on 2008-01-20
please  help?

I'm getting worried I might have screwed things up a little too much...

---

### Post by ispy on 2008-01-20
screw it, I'm just going to clean install Ubuntu, i've already backed up my data. I enjoy tweaking it back to it's original settings anyways. thanks Frup for the info.

---

### Post by frup on 2008-01-20
> **ispy said:**
> please  help?

I'm getting worried I might have screwed things up a little too much...

Firstly the last entry which is puppy and the first are both on the same partition? This is intended?

If you moved the Ubuntu Partition left one, make it hd0,1 and see if that works. Delete the entries of the partitions you deleted. It will be wise to run something like sudo fdisk -l first... maybe post that here.

```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
# CHANGE THE ABOVE LINE maybe to (hd0,1) if you did in fact move the partition left 1.
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=310c5326-e442-4d25-af54-62b7cb6935b3 ro quiet splash locale=en_US
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=310c5326-e442-4d25-af54-62b7cb6935b3 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
#remove this as I think you deleted it.
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows NT/2000/XP
root		(hd0,3)
savedefault
makeactive
chainloader	+1

title Puppy Linux 300 frugal
rootnoverify (hd0,2)
# This is correct?
kernel /puppy300/vmlinuz pmedia=satahd psubdir=puppy300
initrd /puppy300/initrd.gz

```

Also check out the second post in this thread [http://ubuntuforums.org/showthread.php?t=673363](http://ubuntuforums.org/showthread.php?t=673363) ... Might be easier than editing the menu.lst

---

