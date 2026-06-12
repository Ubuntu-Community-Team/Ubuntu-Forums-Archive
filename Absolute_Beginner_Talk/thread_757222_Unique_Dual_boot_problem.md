---
title: "Unique Dual boot problem"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by notjohn101 on 2008-04-16
ok so i got a new (500gb) hard drive and i partioned it as follows

60gb linux
60gb windows
344 docs
1gb swap

i installed windows first and it put every partion except the linux one on a extended partion for some reason

so now when i go to boot windows i get problems

here my fdisk -l 

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cbceb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7833    62918541   83  Linux
/dev/sda2            7834       60801   425465460    f  W95 Ext'd (LBA)
/dev/sda5   *        7834       15666    62918541    7  HPFS/NTFS
/dev/sda6           15667       60669   361486566    7  HPFS/NTFS
/dev/sda7           60670       60801     1060258+  82  Linux swap / Solaris
boys@BOYSCOMPUTERLINUX:~$ 

and my menu.lst

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout		3

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
# kopt=root=UUID=0cb3739c-92d0-45ad-bbc3-77ee2b2b8e45 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0cb3739c-92d0-45ad-bbc3-77ee2b2b8e45 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0cb3739c-92d0-45ad-bbc3-77ee2b2b8e45 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Windows XP
rootnoverify	(hd0,4)
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST


thanks =]

---

### Post by northern lights on 2008-04-16
XP wants to reside in the first partition of the first drive - sda1 or (hd0,0). That's where you've installed Linux.

You've got two options:

1. Reinstall both OSs

2. Remap partitions in GRUB. Check the [GRUB manual]("http://www.gnu.org/software/grub/manual/grub.html#map").

---

### Post by notjohn101 on 2008-04-16
so would it be possible to do
 
map (hd0,0) (hd0,4)
map (hd0,4) (hd0,0)

??

---

### Post by bumanie on 2008-04-16
As previously stated, windows prefers the first partition on  a drive, especially the main drive. I don't think windows can boot from  a logical partition, it needs a primary partition. Therefore any editing you try will not work unless you get windows as a primary partition. You could do this with gparted seeing you only have one primary partition at present. Then mapping etc may work.

---

### Post by notjohn101 on 2008-04-16
i plan to do the mapping.....but ive only seen mapping as

map (hd0) (hd1) and the like

my question would it remap partions


map (hd0,0) (hd0,4) like that

---

### Post by northern lights on 2008-04-16
```
title Windows XP
map (hd0,0) (hd0,4)
map (hd0,4) (hd0,0)
root (hd0,0)
makeactive
chainloader +1
```
should work

---

### Post by notjohn101 on 2008-04-16
will try that now

---

### Post by notjohn101 on 2008-04-16
nope got an error, and i also tried w/ makeactive deleted and it still didnt work

is it possible to delete the extended partition w/o deleting the partitions on it?

---

### Post by notjohn101 on 2008-04-16
bump

.....i guess ill be getting my OS CD's out....

---

### Post by northern lights on 2008-04-17
> **notjohn101 said:**
> .....i guess ill be getting my OS CD's out....

Crap. A lot of time involved there, but if the mapping doesn't work, I'm at the end of my ideas also...

---

### Post by zvacet on 2008-04-17
Let it look like this 


### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP
rootnoverify (hd0,4)
chainloader +1

or 


### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP
map (hd0,0) (hd0,4)
map (hd0,4) (hd0,0)
root (hd0,0)
makeactive
chainloader +1

If this doesn´t work you will have to install Windows on primary partition.Ubuntu can be on exended.Sorry!

---

