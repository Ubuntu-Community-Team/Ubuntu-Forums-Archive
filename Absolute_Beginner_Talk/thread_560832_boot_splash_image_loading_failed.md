---
title: "boot splash image loading failed"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by path_finder on 2007-09-26
Hi,

---

### Post by path_finder on 2007-09-26
Hi,

I tried to edit the grub splash image. Now i am getting this message
"Failed to read splash image ((hd0,3)/boot/Ubuntusplash.xpm.gz) 
Press any key to continue.... "

This is my menu.lst file.

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
splashimage (hd0,3)/boot/grub/debsplash.xpm.gz
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		3

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

 #Pretty colours
#color           black/brown                       blink-yellow/black

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
# kopt=root=UUID=931c8890-f492-4e79-b487-7359464bfb31 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
root		(hd0,3)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=931c8890-f492-4e79-b487-7359464bfb31 ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,3)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=931c8890-f492-4e79-b487-7359464bfb31 ro single
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Warren Watts on 2007-09-26
> **path_finder said:**
> Hi,

I tried to edit the grub splash image. Now i am getting this message
**"Failed to read splash image ((hd0,3)/boot/Ubuntusplash.xpm.gz) **
Press any key to continue.... "

This is my menu.lst file.

......................................
**splashimage (hd0,3)/boot/grub/debsplash.xpm.gz**
............................................


I'm not quite sure I understand how or why you received that particular error, because the error (in bold above) refers to "/boot/Ubuntusplash.xpm.gz", and menu.lst refers to "/boot/grub/debsplash.xpm.gz"

??????

---

### Post by path_finder on 2007-09-27
Actualy this is regarding grub splash not boot splash.
I am so sorry, It was a my mistake. i tried by using both ubuntu.xpm.gz & deb.xpm.gz splash images.
No matter what the name is, it gives same type of error massage. Only change is the name.
So if put debsplash.xpm.gz it gives the message " Failed to read splash image ((hd0,3)/boot/debsplash.xpm.gz
Press any key to continue..."
All these images are specialy designed ones for grub splash.

Thanks.

---

### Post by totalnub on 2007-09-27
yo, maybe it's the lack of an equal sign, or maybe you don't actually have the bootsplash images in the /boot/grub/ directory. also, i've always found where people put the image path like i have in here:

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##
[B][U]
splashimage=(hd0,1)/boot/grub/mac08.xpm.gz[/U][/B]

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0b70a6c1-38fb-43a7-8715-289709beaf6d ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0b70a6c1-38fb-43a7-8715-289709beaf6d ro single
initrd		/boot/initrd.img-2.6.20-16-generic


try that out man gl.

---

### Post by path_finder on 2007-09-28
Its still same.
Fifth line of my menu.lst file is  "splashimage=(hd0,3)/boot/grub/Ren_and_Stimpy.xpm.gz"
Believe me when i check the properties of this particular splash image it says the location is "/boot/grub"  
Please help I am trying to add a splash image to my grub from a very long time..!

---

### Post by Warren Watts on 2007-09-28
> **path_finder said:**
> Its still same.
Fifth line of my menu.lst file is  "splashimage=(hd0,3)/boot/grub/Ren_and_Stimpy.xpm.gz"
Believe me when i check the properties of this particular splash image it says the location is "/boot/grub"  
Please help I am trying to add a splash image to my grub from a very long time..!

file names are case sensitive, so make sure the case (upper/lower) match for the reference in menu.lst and the actual file itself.

---

### Post by path_finder on 2007-09-30
I checked its still the way it was. Root partion is not a primary partion is it a problem?

---

### Post by amrith on 2008-03-15
Even I am facing absolutely the same problem .I tried doing everything as mentioned but doesnt help .Is it because my ubuntu is not in the primary partition ?

---

