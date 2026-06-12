---
title: "[SOLVED] GRUB menu"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by phizikal on 2007-07-01
Ok, I noticed some people talking about the grub menu on reboot. And I don't see any menu at all... I am using dapper, is that why? or what.....

Thanks.

---

### Post by avik on 2007-07-01
Do you have Windows or any other operating system installed?  For the most part, you shouldn't be seeing the menu in the first place.

---

### Post by phizikal on 2007-07-01
No, I have just ubuntu and no dual-booting. How do I make it view the menu? Because incase I need the recovering module.

---

### Post by buuntuu! on 2007-07-01
you'll find it at /boot/grub/menu.lst
open it with your favourite editor (as root) and you can edit it.
here's some [info]("http://users.bigpond.net.au/hermanzone/p15.htm") on grub.

---

### Post by kittyhawk63 on 2007-07-01
Copy and paste into Terminal:
[COLOR=Red] gksudo gedit /boot/grub/menu.lst
[/COLOR] 
A separate page will come up.

You can edit it from there. 

Remember to save.

Ask and I will post mine for you to see.
kh

---

### Post by phizikal on 2007-07-01
Okay, on the menu.lst it says to hit ESC to get the menu. I am gonna reboot and test it.

brb.

*edit to the dude above post yours so i know what to edit. :D

---

### Post by kittyhawk63 on 2007-07-01
> **phizikal said:**
> Okay, on the menu.lst it says to hit ESC to get the menu. I am gonna reboot and test it.
brb.
*edit to the dude above post yours so i know what to edit. :D



[php]# menu.lst - See: grub(8), info grub, update-grub(8)
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST


#I placed Windows XP here. It will default to start automatically. This is for #my wife's use.
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title        Windows XP
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


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
# kopt=root=UUID=7785b6a6-5e7e-4afb-b842-ef267d74a7e0 ro

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

#Note here and elsewhere that I changed the title.
#title        Ubuntu, kernel 2.6.20-16-generic
title        Feisty Fawn 7.04
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=7785b6a6-5e7e-4afb-b842-ef267d74a7e0 ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

#title        Ubuntu, kernel 2.6.20-16-generic (recovery mode)
title        Feisty Fawn 7.04 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=7785b6a6-5e7e-4afb-b842-ef267d74a7e0 ro single
initrd        /boot/initrd.img-2.6.20-16-generic

#title        Ubuntu, kernel 2.6.20-15-generic
#root        (hd0,0)
#kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=7785b6a6-5e7e-4afb-b842-ef267d74a7e0 ro quiet splash
#initrd        /boot/initrd.img-2.6.20-15-generic
#quiet
#savedefault

#title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
#root        (hd0,0)
#kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=7785b6a6-5e7e-4afb-b842-ef267d74a7e0 ro single
#initrd        /boot/initrd.img-2.6.20-15-generic

#title        Ubuntu, memtest86+
#root        (hd0,0)
#kernel        /boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title        Other operating systems:
#root [/php][COLOR=Red]If you have any other questions, don't hesitate to ask.[/COLOR]
[COLOR=Red]kh[/COLOR]

---

### Post by phizikal on 2007-07-01
Gee thanks. :D

---

### Post by kittyhawk63 on 2007-07-01
> **phizikal said:**
> Gee thanks. :D

My pleasure. Make sure you read my two notes above the lines in blue.
kh

---

### Post by phizikal on 2007-07-01
Sure did, i rebooted and it there. Thanks again.

---

### Post by kittyhawk63 on 2007-07-01
> **phizikal said:**
> Sure did, i rebooted and it there. Thanks again.

Remember to mark your thread as "Resolved."
kh

---

