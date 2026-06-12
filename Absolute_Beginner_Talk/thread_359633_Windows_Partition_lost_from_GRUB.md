---
title: "Windows Partition lost from GRUB"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-02-12
When I tried to use my Windows XP a while ago, for some reason, it was not in GRUB's OS list and the choice for Ubuntu as the OS was duplicated.

I do not remember doing anything with GRUB lately.

What would have caused this?

How can I use my Windows XP again?

:guitar:

---

### Post by xyz on 2007-02-12
Let's first see what's in (in a terminal, run):
```
cat /boot/grub/menu.lst

```
Then copy/paste the output here. Thx.

---

### Post by wersdaluv on 2007-02-12
> **xyz said:**
> Let's first see what's in (in a terminal, run):
```
cat /boot/grub/menu.lst

```
Then copy/paste the output here. Thx.

Thanks for the reply. :) 

Here is the code:

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
timeout         3

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
# kopt=root=UUID=d2239123-2d1b-4ffc-b86c-68e0104877c8 ro
# kopt_2_6=root=/dev/hda1 ro

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

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
boot

```

---

### Post by xyz on 2007-02-12
Try this in a terminal:
```
gksudo gedit /boot/grub/menu.lst
```
Copy/paste this if you have XP Pro:
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Professional
(hd0,0)
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1
If you have XP Home:
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1



---

### Post by wersdaluv on 2007-02-12
Thanks. :)

I just have a question. How was my menu.lst edited without me editing it? I am very curious.

---

### Post by xyz on 2007-02-12
You're welcome
> How was my menu.lst edited without me editing it? I am very curious.
I wish I knew!!


PS: Think of making a copy of your "/boot/grub/menu.lst" so that you can easily restore it in case of trouble!

---

### Post by wersdaluv on 2007-02-12
> **xyz said:**
> 
PS: Think of making a copy of your "/boot/grub/menu.lst" so that you can easily restore it in case of trouble!

I guess you are right. Thanks! I will do that.

:guitar:

---

### Post by xyz on 2007-02-12
Just in case...to copy it, in a terminal:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
```
to restore it:
```
sudo cp /boot/grub/menu.lst.old /boot/grub/menu.lst
```
Good luck!;)

---

### Post by geek_Man on 2007-02-12
wersdaluv, you probably had a kernal update or something.

---

### Post by wersdaluv on 2007-02-12
> **geek_Man said:**
> wersdaluv, you probably had a kernal update or something.

Binggo!  I did!

Thanks! :)

---

### Post by xyz on 2007-02-13
> **geek_Man said:**
> wersdaluv, you probably had a kernal update or something.
So did I but Windows is still there!

---

### Post by geek_Man on 2007-02-14
Yeah, but maybe his Windows entry was inside the Debian Automagic area-thingy.

---

