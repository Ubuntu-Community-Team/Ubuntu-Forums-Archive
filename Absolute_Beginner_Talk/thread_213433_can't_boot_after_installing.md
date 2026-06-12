---
title: "can't boot after installing"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by night_day on 2006-07-11
I'm a complete newbie to Linux, but after playing with the demo on the Live CD, I decided to install it.  I threw a second HD on my existing machine and ran the installation on my slave HD.  Installation was prefectly smooth with no problems, but when I reboot after the installation process, I get Error 21 right after the line "GRUB 2.1 initializing" (or something to that effect I am at work and am going off memory hete)  Anyone know what might be the problem?  Thanks!

---

### Post by taurus on 2006-07-11
Boot from the LiveCD again.  Open a terminal by Applications -> Accessories -> Terminal and mount your /boot, assuming it's /dev/hdb1, as
```

sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hdb1 /mnt/ubuntu

```
Now, look in /mnt/ubuntu/grub/menu.lst to see what does it say (or paste it here if you can't make any sense out of it)...
```

more /mnt/ubuntu/grub/menu.lst

```

---

### Post by night_day on 2006-07-11
Hi taurus, thanks for your help.  I did the commands as you displayed, but when I try to view it with 

```
more /mnt/ubuntu/grub/menu.lst
```

There doesn't seem to be a grub subdirectory.  My error is

> /mnt/ubuntu/grub/menu.lst: No such file or directory

No error when I mounted the drive.  Any other suggestions?  Thanks!

---

### Post by SkyNet2029 on 2006-07-11
the syntax is incorrect. No biggie. try this:

```
more /mnt/ubuntu/boot/grub/menu.lst
```

The grub directory tree is located in the /boot partition.

---

### Post by night_day on 2006-07-11
Thanks for that clarification.  Well, I got it to display, I have no idea what I am looking at though!  :)   I've included the whole thing here

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
# password whatever

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
# kopt=root=/dev/hdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title           Ubuntu, kernel 2.6.15-23-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

