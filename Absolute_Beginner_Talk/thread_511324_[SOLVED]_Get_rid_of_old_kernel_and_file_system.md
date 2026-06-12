---
title: "[SOLVED] Get rid of old kernel and file system"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-07-27
I have reinstalled Ubuntu over my old win partition - at the moment grub lists the kernels on this new install and also the kernels from my old install. I was dual booting using seperate HDDs for both OS - I want to get rid of the old kernels and file system by reformatting the OLD root partition to free the space.

1 - can I just comment out the old kernels from menu.lst after reformatting the old root partition, therefore all the lines after the divider

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
# kopt=root=UUID=9be84c49-0750-4aae-844b-4053af769e12 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9be84c49-0750-4aae-844b-4053af769e12 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9be84c49-0750-4aae-844b-4053af769e12 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9be84c49-0750-4aae-844b-4053af769e12 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9be84c49-0750-4aae-844b-4053af769e12 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

[COLOR="Red"]# This is a divider, added to separate the menu items below from the Debian[/COLOR]
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, kernel 2.6.20-16-generic (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=defa6a5f-0949-4f6b-9525-d7874746d155 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=defa6a5f-0949-4f6b-9525-d7874746d155 ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=defa6a5f-0949-4f6b-9525-d7874746d155 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=defa6a5f-0949-4f6b-9525-d7874746d155 ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, memtest86+ (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

2 - what do I need to do to fstab (if anything) to get the new install to recognise it as a partition over which I have rights.


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=9be84c49-0750-4aae-844b-4053af769e12 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=dabb09c2-964c-466d-a039-cde4c30d23f8 /home           ext3    defaults        0       2
# /dev/hdb1
UUID=defa6a5f-0949-4f6b-9525-d7874746d155 /media/hdb1     ext3    defaults        0       2
# /dev/hdb2
UUID=6cebc2cf-6ba9-4c38-bdd8-5abf91ebf7d3 /media/hdb2     ext3    defaults        0       2
# /dev/hda3
UUID=8150326b-3b03-4e2a-bc5b-e0335617f2cf none            swap    sw              0       0
# /dev/hdb3
UUID=adb0de9d-b350-4ece-a75e-e1bf51da0cfa none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

hda is the newly formatted and installed drive - hdb1 is that which I wish to reformat.

---

### Post by FleetAdmiral74 on 2007-07-27
You could try commenting out the unneeded lines. If it does not boot, then you can always just use a LiveCD to get in there and delete the ##'s

---

### Post by Rocket2DMn on 2007-07-27
Do the format, and if you can't see what you need to for the new partition, run
```
sudo fdisk -l
``` and you can modify your fstab file based on that information - you seem to know what you're doing.
I see you posting a lot when you are about to do something to your computer, and it is certainly wise to be prepared for what you're doing, but if I may offer a little advice: just do it.  You will learn a lot by deciding what you want to do, researching how to do it, then making it happen and troubleshooting if you need to.  You seem to know the system well enough that you can think on your feet, so good luck!

---

### Post by forestpixie on 2007-07-27
it boots fine from the right options - I started the first option which is the right kernel on the right drive.

- what I'm really interested in is getting at the to be freed up space - at the moment I've got two lots of file system files - thus the worry about fstab - I know at present as that old root is set for root priveleges and I will want them to be changed.

---

### Post by forestpixie on 2007-07-27
> **Rocket2DMn said:**
> ... just do it , ... so good luck!

I got married like that once :(

but thanks for the vote of confidence - if it gets really hairy people do respond to a cry of HELP here.

I've been waiting to get rid of windows since May - just waiting to get a printer I could use -  :D

---

### Post by forestpixie on 2007-07-28
just posting in case it comes up in a search for someone else :)

deleting the old /root system caused Ubuntu not to start - wouldn't get past a fsck.

booted with gparted - reformatted drive to ext3 

edit fstab to remove instances relating to that drive

restart ubuntu - got UUID for drive

edited fstab to reflect new UUID - made changes to permissions in fsatb and had to follow psychocats chmod instructions.

restarted - all fine now.

thanks to those who answered last 3 threads - :D

---

