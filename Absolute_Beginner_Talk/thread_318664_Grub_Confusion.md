---
title: "Grub Confusion?"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by gingerj on 2006-12-14
Hi all I've literally just installed Ubuntu for the very first time 10 minutes, this forum and the official book have been major help and without them I don't think I would of got this far.

Before I made this thread I checked the official book which I was hoping to be the answer for everything :p But for obvious reasons it can't be written for me :)

So hopefully one of you guys could help me out on this one, I've got a Laptop which the entire family use to google daily.

No one is computer literate in my house and everyone has to be spoon fed the answers for the most basic of things. So now that Ubuntu has installed it's literally gonna cause mayhem due to GRUB taking over the natural order of things.

Basically as I'm sure you guys are away GRUB pauses the boot process, and produces a menu so you can run your desired O/S as there's more than one on my HDD now. 

Is there a way (like lilo) to let GRUB take over for a certain period say like 15 seconds, and if nothing has been manually selected it just boots into windows.

As currently the GRUB menu resembles something like this: UBUNTU, UBUNTU RECOVERY, SOME OTHER RUBBISH, then WINDOWS XP HOME EDITION.

Erm I can safely say this is gonna be to confusing/annoying for my parents especially, so I'd like to rework this if possible.

Cheers and thanks in advance!

---

### Post by mykalreborn on 2006-12-14
type this in a terminal:
```

sudo gedit /boot/grub/menu.lst

```
then search for the phrase "## timeout sec" (it should be on line 20 ;). it will look something like this:
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3
```
the timeout is actually what your interested in. set is at any length you want (under 10 seconds if you want to test your reflexes :p).
then ckick save. and enjoy ^_^

---

### Post by happy-and-lost on 2006-12-14
Change the order of the menu so that the Windows section comes first and change timeout to 15 sec. Post your current menu.lst and I'll show you what to do.

---

### Post by gingerj on 2006-12-14
RIght after doing some reading:

I've managed to find my grub boot file thing.
> 
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
# kopt=root=/dev/hda6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1



I see the word default and the number 0, is that the first item in the list?

i.e. Ubuntu, kernel 2.6.15-23-386 in my case

So all I have to do is count down the list till I reach XP Home edition and type in that number is instead and save?

In my case that would be 4 (5 entries but computers start counting at 0 so that is 4 instead)?

So I do default 4 instead and then does that mean when I reboot, GRUB will highlight this one instead?


Cheers

---

### Post by happy-and-lost on 2006-12-14
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title Microsoft Windows XP Home Edition
root (hd0,1)
savedefault
makeactive
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Windows NT/2000/XP
root (hd0,0)
savedefault
makeactive
chainloader +1

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


title Ubuntu, kernel 2.6.15-23-386
root (hd0,5)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda6 ro quiet splash
initrd /boot/initrd.img-2.6.15-23-386
savedefault
boot

title Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root (hd0,5)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda6 ro single
initrd /boot/initrd.img-2.6.15-23-386
boot

title Ubuntu, memtest86+
root (hd0,5)
kernel /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


```

Should do it

---

