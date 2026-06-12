---
title: "Making Grub pick Ubuntu Auto as default OS."
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by Own3d on 2008-04-16
Hi , I'm running a dual boot at the moment with Vista Home Premium and Ubuntu 7.10 , At the moment when I press on and its gone past the BIOS it comes up with the grub menu showing Ubuntu , Then Ubuntu Recovery Mode, Then Ubuntu Memtest and then under other operating systems Windows Vista. What I would like is it to just load into ubuntu without the menu or me pressing anything. I've heard about ways of making it default to pick the OS of choice. Below is my Menu.lst file. 

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
default		1

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
# kopt=root=UUID=9456f6c6-77a1-4266-8ddc-a26ea729aac5 ro

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9456f6c6-77a1-4266-8ddc-a26ea729aac5 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9456f6c6-77a1-4266-8ddc-a26ea729aac5 ro single
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
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1





Would it be possible for one of you kind people to explain what I should change to make it go into Ubuntu . Thanks

---

### Post by angry_johnnie on 2008-04-16
Uncomment the line that says **hidden menu** (remove the #).
And, also, edit the line that says **timeout** so that it gives you something lower than 10.
If you change it to 1, for example, you'll have only one second to hit escape, before it automatically boots into Ubuntu.
Hitting escape unhides the menu.

---

### Post by kpkeerthi on 2008-04-16
Change the line default 1 to **default 0** to auto select Ubuntu. default 1 selects recovery mode.

---

### Post by philinux on 2008-04-16
I you dont want to edit grub manually, install startupmanager from synaptic. This is a nice gui to change grub options.

I've got my timeout set to 2 seconds. Just long enough to be useful.

---

### Post by Own3d on 2008-04-16
Cheers for the advice , I've changed it and i'm gonna reboot now and test it. Can you change timeout to 0 or is 1 the minimum?

---

### Post by Own3d on 2008-04-16
Wow this is great guys thanks, Problem solved except I want to know if I can change it to timeout 0 or if 1 is minimum, Apart from that most pleased :)

---

### Post by philinux on 2008-04-16
You can use 0.

---

### Post by Own3d on 2008-04-16
Fantastic Great Responses ! I <3 This Forum :D

---

