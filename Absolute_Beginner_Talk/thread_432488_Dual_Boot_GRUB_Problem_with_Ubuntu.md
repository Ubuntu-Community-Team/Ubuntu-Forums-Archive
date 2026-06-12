---
title: "Dual Boot GRUB Problem with Ubuntu"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by AlvinMartin on 2007-05-04
Hello,

I wonder if someone can help me.  I have XP machine on which I installed Ubuntu Linux into a partition on an external USB HDD.  The installation process was fine, but when the mahine reboots I get the problem with dual-booting using GRUB - it's hanging with Error 25 during/after Stage 1.5.  At the moment I'm booting Linus from the Live CD disk.

I believe I followed the Ubuntu installation instructions with regards to partitioning, but I'm a Linux novice, so I have probably done something wrong.

The disk partitions are thus;

Disk 1 (on board SATA HDD) - this is the Windows installation disk.
/dev/sda1	fat16	62MB
/dev/sda2	ntfs	72GB	(boot)
/dev/sda3	fat32	 3GB

Disk 2 (USB HDD)
/dev/sdb1	ntfs		/media/Home PC	73GB	#This was (and still is off disk storage for XP)
/dev/sdb2	ext3		/media/disk	48GB	#This is where I installed Ubuntu
/dev/sdb4	linux-swap			 2GB
/dev/sdb3	ntfs		/media/Acom	87GB	#This is more off disk storage.

My gut feeling is that this partitioning scheme is wrong, and is at least one of my problems.  I have a device.map file, and a menu.lst file.  Both of these are physically stored in /media/disk/boot/grub - I'm not sure if that is right.

The contents are

##################################################################################################
device.map
(hd0,1)	/dev/sda2
(hd1,1)	/dev/sdb2

##################################################################################################
menu.lst
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
timeout		30

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
# kopt=root=UUID=f4fe7877-ad42-4985-9eb7-2f07afa26d3d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f4fe7877-#ad42-4985-9eb7-2f07afa26d3d ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f4fe7877-#ad42-4985-9eb7-2f07afa26d3d ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1
###########################################################################################################

I'd really appreciate some suggestions on what I'm doing wrong.

Thanks, Stretch.

---

### Post by Kobalt on 2007-05-04
Maybe Grub insn't properly installed on your USB Drive mbr, you should try to reinstall it either on the mbr, or on your first hard drive.
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

### Post by AlvinMartin on 2007-05-04
Thanks, I'll try it.

Does the partitiong scheme, menu.lst file and device.map file look correct to you?

Stretch

---

### Post by freebird54 on 2007-05-04
I don't see anything wrong per se.  It looks like a reasonable chain of decisions, and possibly correct entries.  The only thing that occurs to me is to ensure that the disks are correctly identified in the menu.lst file.  To do this, from the Live CD, open a terminal and run:

```
sudo vol_id -u /dev/sdb
```

which should give you UUID of the partition.  If this is giving you trouble, try changing the meu.lst to NOT use the UUID, thus giving you line that looks thus:

```
kernel /boot/vmlinuz-2.6.20-15-generic root=/dev/sdb2 ro quiet splash
```

The UUID method is preferred (incase of drive availability changes - but the old way works just fine for most.

Hope this helps..

(My thought is that partitions changed since grub was installed)

---

### Post by AlvinMartin on 2007-05-04
Thanks for this.  I'll try it.

---

