---
title: "Newbie Dual Boot Questions"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by fatsheep on 2006-07-21
#1: When I bootup the default option is to boot to Ubunutu.  This is fine, but say I install Suse later on (which I intend to) and it places itself as the default boot operating system.  How do I change it around so Ubuntu is default?
#2: Ever since I've updated there have been two kernel options on bootup, can I just delete the older kernel or is that a bad idea?

---

### Post by Paerez on 2006-07-21
You can delete the older kernel if the new one works. All of this stuff can be set in "/boot/grub/menu.lst" including the default OS and which OSes are in the list. But **be careful** because if you do something wrong your OS will be unbootable.

If you post us your /boot/grub/menu.lst, we can help you edit it so nothing goes wrong.

---

### Post by Jagot on 2006-07-21
1) [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

2) You can remove the old kernel using Synaptic - it is quite safe to do so as long as you're sure everything works with the new kernel.

---

### Post by monkieie on 2006-07-21
> **fatsheep said:**
> #1: When I bootup the default option is to boot to Ubunutu.  This is fine, but say I install Suse later on (which I intend to) and it places itself as the default boot operating system.  How do I change it around so Ubuntu is default?
#2: Ever since I've updated there have been two kernel options on bootup, can I just delete the older kernel or is that a bad idea?

can't say that I have all that much experience but have you seen this link? Might help you out a bit...

[http://ubuntuforums.org/showthread.php?t=111215&highlight=reset+dual+boot](http://ubuntuforums.org/showthread.php?t=111215&highlight=reset+dual+boot)

---

### Post by fatsheep on 2006-07-21
Thanks for the fast responces.  About removing the old kernel, I still don't understand how to do it.  I'm in synaptic and I went to the base system category and the only installed packages are:

> linux-restricted-modules-amd64-generic
Restricted Linux modules on x86_64.

and

> linux-amd64-generic
Complete Linux kernel on x86_64.

:confused: 


About the first question, here's my menu.lst file.  In bold is what I think I can safely remove.  Please correct if I'm wrong.

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
# kopt=root=/dev/hdc2 ro

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

title		Ubuntu, kernel 2.6.15-26-amd64-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/hdc2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/hdc2 ro single
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
boot

[B]title		Ubuntu, kernel 2.6.15-23-amd64-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/hdc2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-amd64-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/hdc2 ro single
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
boot[/B]

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
# on /dev/hdc1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


---

### Post by Jagot on 2006-07-21
Your old kernel should be something along the lines of linux-image-2.6.15-23-amd64-generic.

Mark that for complete removal in Synaptic.

When you remove an old kernel it's entry in GRUB will automatically be removed so you don't need to mess around with it manually.

---

### Post by crossedout on 2006-07-21
If you are uncomfortable about uninstalling the old kernels you can simply hide the extra GRUB menu choices by editing menu.lst.

[PHP]sudo gedit /boot/grub/menu.lst[/PHP]
Then put the # symbol in front of the options you want to hide.

Note: When the kernel is updated it will probably reset those choices back into the menu so you may have to edit the menu.lst again.  Also, its a good idea to keep an old one available as a backup.

-crossedout

---

### Post by fatsheep on 2006-07-21
Ah I found the old kernel in synaptic, uninstalling it now.  Thanks guys. :p

---

### Post by djsroknrol on 2006-07-21
Fatsheep...

look for this to change the default OS:

```
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
[B]default 0
[/B]
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
```

The first OS in menu.lst is always 0, the next one is 1, etc..so all you have to do is edit menu.lst to what OS you'd like to boot to by changing that line..

---

