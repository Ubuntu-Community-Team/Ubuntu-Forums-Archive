---
title: "Need some serious help"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by elcapy on 2007-03-30
Ok i will try to explain i did the whole partioning thing and everything works fine running ubuntu but can't boot to windows ([COLOR="Red"]unmountable bootvolume message[/COLOR]) XP Pro i actually dont want to use it, I love this linux OS even though i'm new to this i love it, but i need for my girl to do her school in work XP so if anyone can help me get the bootloader working for both OS i appreciate it very much.

Now the thing is i did not see Grub installation or a bootloader option to install so i don't know what's going on I'm clueless.  I apologize if i sound like i dont know what i'm doing but i really don't know much about ubuntu been using it for  three days now and search for the fix to the bootloader but some reason can't  find anything that works for me. thanks all in advance Berto

---

### Post by joethenoob on 2007-03-30
During the install, you are asked to either use the entire disk, largest unused space or manually partition. Do you remember which you picked?

---

### Post by drs305 on 2007-03-30
I won't be around the computer long enough to answer, but if you can tell us if you have a /boot/grub folder it will help those that read this post. If you do, posting the content of /boot/grub/menu.lst would also be helpful.

---

### Post by elcapy on 2007-03-30
yeah i picked manually because i had made the linux partitions already

---

### Post by Sandlst on 2007-03-30
So when do you see the error message?  Also, I assume your ubuntu installation is working, please open a terminal (Applications/Accessories/Terminal) and type in ```
sudo fdisk -l
```Post back the output of this please.  Secondly, type in ```
gedit /boot/grub/menu.lst
``` and please post it in here, between code lines, using the # button when making a reply.  These should help us figure out what the trouble is hopefully.

---

### Post by elcapy on 2007-03-30
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
# kopt=root=/dev/hdd2 ro

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

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hdd2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hdd2 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdd2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdd2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdd1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


I hope this help this is what the grub menu list says

---

### Post by Michl on 2007-03-30
Did you manually partition or guided partitioning?  I did a guided
install several times and never had to worry about grub and
automatically get the grub menu with Windows XP as a choice.

(My favorite way of doing it is with two harddrives, but it also
worked with Windows XP on one drive.)  DId you defragment
first?  The other thing I did (and I am shooting in the dark here)
is first load Windows with useless files so that there wouldn't
be so less continuous free space available for ubuntu, but
I would nt have to do it manually.  Then once ubuntu is installed,
I went back to Windows XP and freed-up several gigabytes.

By the way, for what it is worth, you can do quite a bit with
open office that you can save in formats that are compatible
with Windows (doc, xls, pdf and so on).

---

### Post by dstew on 2007-03-30
elcapy:

We also need your **fdisk -l** printout.

---

### Post by elcapy on 2007-03-30
what's the fasted way to find the fdisk file i don't see in xp folders

---

### Post by elcapy on 2007-03-30
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect



this is what i have for Win boot.ini

---

### Post by joethenoob on 2007-03-30
> **Michl said:**
> 
(My favorite way of doing it is with two harddrives, but it also
worked with Windows XP on one drive.)  DId you defragment
first?  The other thing I did (and I am shooting in the dark here)
is first load Windows with useless files so that there wouldn't
be so less continuous free space available for ubuntu, but
I would nt have to do it manually.  Then once ubuntu is installed,
I went back to Windows XP and freed-up several gigabytes.


I don't think that's how the install utility works. When it talks about free space, it is referring to unpartitioned space on the drive. Does adding/deleting gigs of files really help?

---

### Post by elcapy on 2007-03-30
Just in case you guys wonder what i did i had 104 gig unpartitioned so i used that instead and split into 40 for linux install and 4g for swap and 60 for fat32

---

