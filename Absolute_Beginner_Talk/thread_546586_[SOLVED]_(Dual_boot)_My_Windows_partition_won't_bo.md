---
title: "[SOLVED] (Dual boot) My Windows partition won't boot anymore. I can still see my Wind"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by mahasmb on 2007-09-09
Gah, this is annoying and more than inconveniencing.

I have a dual boot with Windows XP and Ubuntu Feisty Fawn. Everything was fine yesterday, and then I tried fixing my Compiz-Fusion problems. I swear I didn't touch anything relating to GRUB or my menu.lst file or anything like that.

Anyways, Windows XP disappeared from GRUB. I tried editing my menu.lst file to get Windows to boot up again, but it just always give me an error, telling me it can't find it. My Windows is under "hda1" and I've tried booting everything from (hd0,0) to (hd0,5) with GRUB to no avail. Here's my editted menu.lst file.

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
timeout		30

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
# kopt=root=UUID=3a422db9-96e6-473a-ad20-f5aa03c2985b ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=3a422db9-96e6-473a-ad20-f5aa03c2985b ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-386
savedefault

title		Ubuntu, kernel 2.6.20-16-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=3a422db9-96e6-473a-ad20-f5aa03c2985b ro single
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=3a422db9-96e6-473a-ad20-f5aa03c2985b ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=3a422db9-96e6-473a-ad20-f5aa03c2985b ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.17-11-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=3a422db9-96e6-473a-ad20-f5aa03c2985b ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-386
savedefault

title		Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=3a422db9-96e6-473a-ad20-f5aa03c2985b ro single
initrd		/boot/initrd.img-2.6.17-11-386

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=3a422db9-96e6-473a-ad20-f5aa03c2985b ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=3a422db9-96e6-473a-ad20-f5aa03c2985b ro single
initrd		/boot/initrd.img-2.6.15-28-386

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=3a422db9-96e6-473a-ad20-f5aa03c2985b ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=3a422db9-96e6-473a-ad20-f5aa03c2985b ro single
initrd		/boot/initrd.img-2.6.15-26-386

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin

title		Windows XP Home
root		(hd0,1)
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root
# This entry automatically added by the Debian installer for a non-linux OS
# on /media/hda1
title 		Windows XP Home
root 		(hd0,1)
#savedefault
makeactive
chainloader 	+1




```

Please help.

---

### Post by alienexplorers on 2007-09-09
The only thing I can see that is different than in my menu.lst is that I do not have savedefault disabled.  Also you have windows listed twice, is there a reason for this.  The one at the bottom is enough.

---

### Post by Warren Watts on 2007-09-09
```
[B]title		Windows XP Home
root		(hd0,1)
makeactive
chainloader	+1[/B]

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root
# This entry automatically added by the Debian installer for a non-linux OS
# on /media/hda1
[B]title 		Windows XP Home
root 		(hd0,1)[/B]
#savedefault
[B]makeactive
chainloader 	+1[/B] 
```
Looking at the menu.lst file you posted, you have TWO entries (in bold above) for Windows XP in there.  Take one of them out and try (hd0,0) assuming you originally had just WinXp in the computer

---

### Post by mahasmb on 2007-09-09
*Sighs*

I got it to work. It was an easy fix. If only I had figured it out in the first 15-30 minutes. It turns out it was inded in **(hd0,0)**, although I thought I had checked that. 

The reason I have Windows in twice was because I have a feeling that the second last Windows entry may get deleted again (that's where I had it before), I'm not sure. So I'm keeping it there as a test, just to see what happens over time.

Overall, problem solved, but why did Windows get deleted from my menu.lst file in the first place??

Thank you very much for your help.

---

### Post by Warren Watts on 2007-09-09
There was a kernel update the other day that re-wrote my menu.lst file and took out two other entries I had in there for FreeDOS and Wolvix Cub.  I had made a backup of the file a few days before when I was editing it for something else, so all I had to do was copy the entries back into the new file.

Since then I make sure I always have a backup copy called menu.lst.bak or something similar on hand just in case...

BTW, you are quite welcome for the help...  That's what this forum is for!  :-)

---

