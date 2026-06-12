---
title: "Default boot settings, need help please"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by bonesoflondon on 2006-08-09
Hi can any tell me what I must change in order for xp to be first in the boot order,I did try changing 

## default num .............to this 
## default 3 but it did nothing
Also when I boot up laptop its shows to installations of Ubunuta is this normal?
I am new to the Linux experince and need some baby sitting until I have learnt a bit,I have googled for several hours and have tried to 
follow this  

[http://www.ubuntuforums.org/showthread.php?p=1340581](http://www.ubuntuforums.org/showthread.php?p=1340581)
,but I am obiviously doing something wrong

Regards Toni



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
default     X_sequence

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
# kopt=root=/dev/hda7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda7 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda7 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda7 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda7 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Tomosaur on 2006-08-09
Well for starters, Grub counts from zero. The first item in the menu is, therefore, 0. Second item is 1, etc. You need to set the 'default' line to a number, eg: 'default     0' or 'default    1'. You can also set it to 'default    saved', and it will load whichever menu item has 'savedefault' in it.

Altering the actual order of the menu items is a copy and paste job, but I personally don't recommend it. It'll only get overwritten again next time your kernel updates or something like that. The easiest way to get Windows to load by default is to just set it load by default, rather than trying to put it first in the menu.

EDIT:

Also, the line you need to edit is not the '## default num' line, it's the one where you currently have 'default X_sequence'.

And yes, showing two installations of Ubuntu is normal. It's not actually two seperate installs, it's two 'kernels', which is basically all the drivers and whatnot to get linux running. The reason you have two (and will get more in the future), is that if the newest kernel has problems, you can load an older, working one and remove the latest one until a new, stable release comes out.

---

### Post by bonesoflondon on 2006-08-09
so 

default X_sequence

becomes

default 1_sequence

is that correct in order for xp to first choice of automatic booting???

Thanks For such a speedy response Toni

---

### Post by Tomosaur on 2006-08-09
Uhh nope. It should just be:

'default 6'. 

Out of interest, why do you think you need the '_sequence' on the end?

XP is the 6th item in your menu.lst (counting from 0, and including the 'Other Operating Systems' seperator).

---

### Post by bonesoflondon on 2006-08-09
Out of interest, why do you think you need the '_sequence' on the end?

I really have zero knowledge about Linux at the moment and any thing I seem to try and do for linux is copy and paste from other pages.
I really need to get a grasp of the very basics


Thanks for you Help 

Toni

---

### Post by Tomosaur on 2006-08-09
Haha yeah, I guess it's pretty confusing. Luckily, there's a lot of help around. If you have any more problems, just ask on this forum I guess.

---

