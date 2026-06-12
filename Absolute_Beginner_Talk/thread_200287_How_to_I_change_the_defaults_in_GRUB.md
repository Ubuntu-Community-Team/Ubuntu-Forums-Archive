---
title: "How to I change the defaults in GRUB?"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by n00b@linux on 2006-06-20
I've got a dual boot XP/Ubuntu laptop which my wife also uses.
My wife is, well, not very PC literate.  She knows how to press the power button and how to point and click on the icon that says "Internet".  I AM being serious.  She freaks out at anything that doesn't look like XP, so I wanted to change the GRUB options so that M$ XP is the default OS (eek!)

I knew how to do this using YaST on SuSE but I'm new to Ubuntu and can't see a bootloader option in any of the System menus.

Can someone help me out here please?

---

### Post by aysiu on 2006-06-20
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by kwaanens on 2006-06-20
sudo gedit /boot/grub/menu.lst

You see "default 0"? Change this to the number for XP. Numbering starts from 0. If I were to set mine to XP, it would then be 5 (see menu.lst pasted in here).

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/sda7 ro

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

title           Ubuntu, kernel 2.6.15-25-686
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.15-25-686 root=/dev/sda7 ro quiet splash
initrd          /boot/initrd.img-2.6.15-25-686
savedefault
boot

title           Ubuntu, kernel 2.6.15-25-686 (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.15-25-686 root=/dev/sda7 ro single
initrd          /boot/initrd.img-2.6.15-25-686
boot

title           Ubuntu, kernel 2.6.15-25-386
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.15-25-386 root=/dev/sda7 ro quiet splash
initrd          /boot/initrd.img-2.6.15-25-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.15-25-386 root=/dev/sda7 ro single
initrd          /boot/initrd.img-2.6.15-25-386
boot

title           Ubuntu, memtest86+
root            (hd0,6)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1

```

---

### Post by aysiu on 2006-06-20
kwaanens, wouldn't it be 6? Doesn't this count as an entry, too, even though there's no operating system for it? ```
title           Other operating systems:
root
```

---

### Post by kwaanens on 2006-06-20
I'm pretty sure you're right. I guess it's just too early in the morning for me :)

- Ketil

---

### Post by stig on 2006-06-20
[QUOTE=aysiu]kwaanens, wouldn't it be 6? Doesn't this count as an entry, too, even though there's no operating system for it? ```
title           Other operating systems:
root
```[/QUOTE]

And what about memtest? I had a dual disk PC (Win98 and Ubuntu Dapper 6.06) set up and booting OK since the Dapper install recently. It was set to default = 4 to boot Win98 but suddenly started booting into memtest instead. I went to the grub file and found a line for memtest had been added before Win98, so I had to change the default to 5.

Where did the memtest come from? I didn't put it there. Would it have come through one of the Ubuntu automatic updates, perhaps?

It seems spooky when boot order suddenly changes!

---

### Post by n00b@linux on 2006-06-20
Thanks everyone.  I did as you said and it's working a treat.  Cheers

---

### Post by kwaanens on 2006-06-20
[QUOTE=stig]Where did the memtest come from? I didn't put it there. Would it have come through one of the Ubuntu automatic updates, perhaps?

It seems spooky when boot order suddenly changes![/QUOTE]

Memtest comes standard with Ubuntu installation, doesn't it?
But there must be a bug in a package, because Grub is supposed to be updated automagically when a package alters menu.lst. When you install a new kernel version it is set up to boot with this, except when you have edited menu.lst manually to boot with something else.

- Ketil

---

### Post by stig on 2006-06-20
[QUOTE=kwaanens]Memtest comes standard with Ubuntu installation, doesn't it?
But there must be a bug in a package, because Grub is supposed to be updated automagically when a package alters menu.lst. When you install a new kernel version it is set up to boot with this, except when you have edited menu.lst manually to boot with something else.
- Ketil[/QUOTE]

Sorry, but I made a mistake about it being memtest - that must have been there  already. On the next boot I still needed to set default bya futher 1, i.e. set it as 6. The problem is due to a new kernel image, not memtest.

The grub file now has:
Ubuntu, kernel 2.6.15-25-386
Ubuntu, kernel 2.6.15-25-386 (recovery mode)
Ubuntu, kernel 2.6.15-23-386
Ubuntu, kernel 2.6.15-23-386 (recovery mode)
Ubuntu memtest
Other OS
Windows 98

So, yes, perhaps there is a bug because I have not edited the file other than changing the default = 0. This could really worry people who have recently set up Ubuntu alongside Windows - I got a shock when I saw the blue memtest window - I'm not familiar with memtest and I thought there must be something real bad happening to the PC!

---

