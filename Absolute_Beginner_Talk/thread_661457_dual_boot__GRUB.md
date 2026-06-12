---
title: "dual boot / GRUB"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by archon123 on 2008-01-07
I just installed Ubuntu on my laptop. I partitioned my hard drive so that I can dual boot. But when I start my computer I get a message saying "loading GRUB please wait" and then the computer goes straight into Ubuntu. How can I get it to boot into Windows?

---

### Post by erginemr on 2008-01-08
Can you please post your "/boot/grub/menu.lst" file here, and also your "/etc/fstab" file?

EDIT: Well, two more; the output of the following two commands from a terminal:
```
blkid
```
```
sudo fdisk -l
```

---

### Post by Panayotis on 2008-01-08
I have the same problem as archon 123

I get the following :

 menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=52becd9a-0d1e-4160-8b73-14957154c0bc ro

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
# defoptions=quiet splash locale=el_GR

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=52becd9a-0d1e-4160-8b73-14957154c0bc ro quiet splash locale=el_GR
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=52becd9a-0d1e-4160-8b73-14957154c0bc ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=52becd9a-0d1e-4160-8b73-14957154c0bc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=48847013-e855-43c2-95ad-3efb13e4a53a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


panayotis@panayotis-laptop:/etc$ blkid
/dev/sda1: UUID="52becd9a-0d1e-4160-8b73-14957154c0bc" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="48847013-e855-43c2-95ad-3efb13e4a53a" TYPE="swap" 
panayotis@panayotis-laptop:/etc$ blkid


  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris


Hope i didnt destroy my Windows XP

Thank you in advance !!!

---

### Post by bumanie on 2008-01-08
From the output of /etc/fstab, it looks as though you may have wiped your windows install. There is no indication that there is an ntfs partition on the disk. You could try to recover this with a program called test disk.
It would be helpful as the above post says to post output of fdisk -l. Also if you can open the live cd partition editor or use gparted live cd and post a screenshot of your hard drive partitions. This will confirm whether you have in fact wiped you windows partition or whether it is not being seen for some reason (this is unlikely).

---

### Post by erginemr on 2008-01-08
I am afraid I have to agree with bumanie. Possibly, you have installed Ubuntu on to your Windows partition during the installation by letting ther installer to gor for a "guided" install (namely, use the complete hard disk for Ubuntu) - hopefully not-.

Checking your hard drives with the Ubuntu Live CD is a good idea to confirm this. And also, the command "sudo fdisk -l" will also reveal how much space each partition occupies, so that you can compare this value with your total hard drive capacity.

---

### Post by browndruid on 2008-01-08
In the case that you did wipe the windows partition, it was probably due to the Ubuntu partition manager, which is not always 100% successful.

A more reliable method would probably be using the tutorial [here]("http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/"), which uses the Linux Rescue Disk to set up the partitions. The only problem is that it's designed to add an Ubuntu partition onto an already installed Windows one, so it may require you to start from scratch. I don't know of any tutorials that show adding Windows onto Ubuntu.

---

### Post by Panayotis on 2008-01-08
Well, I trusted the first method where the installation of Ubuntu is done automatically letting windows too, I dont know what went wrong.

I had two hard disks (total 120) the one with Windows was Fat32 !!!

Acer has a hidden place for windows backup. This is what i get from fdisk -l :

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd3efffc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

I think sda2 corresponds to the backup of acer.

Can I reboot from it so I install again windows.

---

