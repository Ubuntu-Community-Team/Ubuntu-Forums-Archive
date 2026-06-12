---
title: "Boot Problem"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by waste301 on 2007-12-05
Hi, fairly new user here.  My problem is this, I have a dual boot that usually works fine, GRUB asks me if I want Ubuntu or Windows, and unless I'm gaming its ubuntu. Suddenly, ubuntu has stopped booting.  I select it and Now loading appears foerever, after a few minutes I have to power down the computer and restart.

If I selesct ubuntu generic, it boots to a command prompt (which I don't know how to use) however typing "QUIT" exits the prompt and brings me to my regular ubuntu logon, which I did and am now posting this message.  Everything seems to be fine, but I don't want to turn of my PC and risk it agin, until I have some feedback.

So! Thanks to anyone who reads this and has any suggestion.

-Matt

---

### Post by waste301 on 2007-12-05
bump

---

### Post by waste301 on 2007-12-05
bump

---

### Post by waste301 on 2007-12-05
OK - can someone please help me?  I don't want to have to use windows for my work, but can't have a PC where its that hard to boot into ubuntu.

---

### Post by waste301 on 2007-12-05
bump

---

### Post by metalheart on 2007-12-05
What do you mean by saying 'dual boot that usually works fine'. Is this the first time you experienced the situation you described?

Execute the following command, to list your boot configuration file

```
cat /boot/grub/menu.lst
```

and post it's contents.

---

### Post by waste301 on 2007-12-05
[I]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=b9cecab8-593a-4656-a240-9b6cbbb529b0 ro

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

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=b9cecab8-593a-4656-a240-9b6cbbb529b0 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=b9cecab8-593a-4656-a240-9b6cbbb529b0 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=b9cecab8-593a-4656-a240-9b6cbbb529b0 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=b9cecab8-593a-4656-a240-9b6cbbb529b0 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

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
[/I]

here it is.  Ubuntu won't boot normally.

---

### Post by metalheart on 2007-12-05
I see no errors in the menu. Are you selecting the first entry titled
```
Ubuntu, kernel 2.6.20-16-generic
```
and it stops?
If this happened only once, then I see no problem. Just shut down your computer and try again.

---

### Post by waste301 on 2007-12-05
I'lll try and boot again, maybe it fixed its self.

---

### Post by waste301 on 2007-12-05
I can't boot into ubuntu.  It jt says "Now Loading" forever.

I booted into "generic" and it logged me into a command prompt.  Now that no longer works.

Help please.

---

