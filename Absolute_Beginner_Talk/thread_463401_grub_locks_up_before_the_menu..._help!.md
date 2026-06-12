---
title: "grub locks up before the menu... help!"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by ouch67 on 2007-06-03
I've been trying to install ubuntu for about a week now dealing with problem after problem, and I'm getting sick of it.

but that's besides the point. I now can't boot my computer because grub comes up saying it's started but then thats it, nothing else happens...

I've check the device.map and menu.lst files and they seem to look ok.

below is the files in question, thanks for any help you can give:

computer specs:

asus p4c800e deluxe
p4 2.8ghz prescott
1gb 3200 pny ram
radeon 9700 pro 128mb
audigy 2 ZS (platinum)

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         783     6289416   55  EZ-Drive

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14592   117210208+  55  EZ-Drive

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       24316   195318238+   7  HPFS/NTFS
/dev/sdd2   *       24317       30146    46829475   83  Linux
/dev/sdd3           30147       30401     2048287+   5  Extended
/dev/sdd5           30147       30401     2048256   82  Linux swap / Solaris

device.map:

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdd

menu.lst:

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
# kopt=root=UUID=74a07eb5-a167-46b5-8e70-4ba6c63dc390 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,1)

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
sudo chmod 777 *
## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=74a07eb5-a167-46b5-8e70-4ba6c63dc390 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=74a07eb5-a167-46b5-8e70-4ba6c63dc390 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd2,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by ouch67 on 2007-06-03
well any ideas?

---

### Post by drs305 on 2007-06-03
I generally stay away from these issues and let the experts handle them, but since you are waiting for someone: are you sure the UUIDs are correct. Repartitioning and reformatting drives can change the UUIDs. I that is a possibility, try using the /dev addresses.

---

### Post by confused57 on 2007-06-03
I don't know anything about "EZ-Drive" or what effect it may have...the only thing I can think of that you can try is to use the live cd to install grub to your (hd2) mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
if your bios is able to boot first to this drive, you should get a grub boot menu...if you do, highlight your Ubuntu entry, press "e", change root from (hd2,1) to (hd0,1), then press "b" to boot...this is a temporary change, but you can see if it works.

---

### Post by drs305 on 2007-06-03
I have had success using Super Grub Disk. It analyzes and repairs all sorts of boot errors. The main site is down I believe but the following site has the information and link to a mirror to download the disk iso.  From what I remember, the information you need is mostly on the disk. It's not easiest process but if I could figure it out I'm sure you can if it's boot related and not something specific to ubuntu.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.htm](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.htm)


Disk mirror:
[http://sgd.howto-linux.de/](http://sgd.howto-linux.de/)

---

