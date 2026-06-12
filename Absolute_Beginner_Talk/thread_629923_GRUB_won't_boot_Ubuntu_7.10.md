---
title: "GRUB won't boot Ubuntu 7.10"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by Genecks on 2007-12-02
I cannot get GRUB to load Ubuntu 7.10

First I had Debian Etch installed. It seemed to do a multi-boot well with XP.
However, I recently installed Ubuntu 7.10 and it seems everything went to hell after that.

I have Debian etch on /dev/sda8
I have Ubuntu Gutsy on /dev/sda11
XP has the first partition

Currently, it seems I'm booting from the menu.lst inside of Debian.
I tried altering the menu.lst file, but nothing seems to be working
It seems like it can't find the proper files.
I don't know exactly what the proper files would be to boot ubuntu 7.10

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

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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
# defoptions=

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title		Debian GNU/Linux, kernel 2.6.23-9
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.23-9 root=/dev/sda8 ro 
savedefault

title		Debian GNU/Linux, kernel 2.6.23-9 (single-user mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.23-9 root=/dev/sda8 ro single
savedefault

title		Debian GNU/Linux, kernel 2.6.22-3-486
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.22-3-486 root=/dev/sda8 ro 
initrd		/boot/initrd.img-2.6.22-3-486
savedefault

title		Debian GNU/Linux, kernel 2.6.22-3-486 (single-user mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.22-3-486 root=/dev/sda8 ro single
initrd		/boot/initrd.img-2.6.22-3-486
savedefault

title		Debian GNU/Linux, kernel 2.6.18-5-486
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.18-5-486 root=/dev/sda8 ro 
initrd		/boot/initrd.img-2.6.18-5-486
savedefault

title		Debian GNU/Linux, kernel 2.6.18-5-486 (single-user mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.18-5-486 root=/dev/sda8 ro single
initrd		/boot/initrd.img-2.6.18-5-486
savedefault

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

[COLOR="Red"]#
# on /dev/sda11
title		Ubuntu Linux 7.10 
root		(hd0,10)
kernel		/vmlinuz root=/dev/sda11 ro
initrd		/initrd.img
savedefault[/COLOR]

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by bumanie on 2007-12-03
To get help with this, it would be helpful if you posted a sudo fdisk -lu output and also described the set up of your computer re how many hard drives and partitions etc. as you seem to have many partitions
This extra information will help someone get to the bottom of your problem.

---

### Post by dadawan on 2007-12-03
> I cannot get GRUB to load Ubuntu 7.10

First I had Debian Etch installed. It seemed to do a multi-boot well with XP.
However, I recently installed Ubuntu 7.10 and it seems everything went to hell after that.

Genecks,
  
  Can you describe the [COLOR="Red"]**hell**[/COLOR] a little better?   Is Ubuntu not showing up in the list?  Do you see it but it will not boot.  An error message perhaps?

  You can type 'c' in grub to go into command mode.  Then you get a prompt where you can type 'help'.   Google around a little bit to figure out how to find out more about grub commands. But you should be able to get grub to tell which config file it is using, and search partitions for others...

-Kevin

---

