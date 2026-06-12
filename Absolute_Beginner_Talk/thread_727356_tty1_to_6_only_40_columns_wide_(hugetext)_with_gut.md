---
title: "tty1 to 6 only 40 columns wide (hugetext) with gutsy and thinkpad T40"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by Tim from Tang on 2008-03-17
Hi All,
I hope somebody can help me. I have just installed the gutsy gibbon on my thinkpad T40  as I was installing a toshiba tecra M1 with it for my daughter (another sad story for another forum). Everything so far is going great excepting that when I wish to go to a virtual console ctrl+alt+F1 to F6 I get only 40 characters wide on the screen with very large text, I have not succeeded to log in on a virtual console either but this may just be because I can not see the display. 
Looking forward to a solution
Tim from Tang

---

### Post by spiderbatdad on 2008-03-17
I believe this resolution is set by grub during boot. You could edit /boot/grub/menu.lst on the kernel line by adding vga=792 if you want 1024x768 for 24 bit.

[https://help.ubuntu.com/community/ChangeTTYResolution](https://help.ubuntu.com/community/ChangeTTYResolution)

---

### Post by Tim from Tang on 2008-03-17
Hi Spiderbatdad,
I tried editing the /boot/grub/menu.lst 
and adding various settings for vga, all with no positive effect sadly. I have no splash screen on boot up either. any other ideas?

---

### Post by spiderbatdad on 2008-03-17
could you post a copy of menu.lst as edited?

---

### Post by Tim from Tang on 2008-03-18
Hi Spider, thanks for sticking with me,
here is the menu.lst
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
# kopt=root=UUID=ea2d5ca6-23ea-4141-8d8c-1f85b5cf8c02 ro

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ea2d5ca6-23ea-4141-8d8c-1f85b5cf8c02 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ea2d5ca6-23ea-4141-8d8c-1f85b5cf8c02 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Many thanks for your help
Tim

---

### Post by Tim from Tang on 2008-03-18
Hi Spiderbatdad,
By the way,
How do I include things like my menu dot list in those nice scrolling boxes I see on other posts?
Thanks
Tim

---

