---
title: "Grub sees XP partition but unbootable"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by moomintroll on 2007-02-27
I'm new to this and would like to install Ubuntu and get rid of XP but my other half wont let me - she says she wants her email back and I seem to have lost XP.

I have two hard drives - 1 for windows and Ubuntu - dual boot and 1 for data

HDA1 has windows in the first partition and Ubuntu Edgy ultimate in the 2nd.  After Ubuntu is installed (which is great by the way) I can now no longer boot in to XP.  Grub sees XP as the OS in its list but after a momentary blip of the XP splash screen it reboots.

I show my grub menu.lst below

Thanks for the help!!

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
# kopt=root=UUID=1b1ff971-080b-4e33-b1af-429181be0846 ro
# kopt_2_6=root=/dev/hda2 ro

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

title        Ubuntu, kernel 2.6.17-11-generic 
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro quiet splash
initrd        /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title        Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro single
initrd        /boot/initrd.img-2.6.17-11-generic
boot

title        Ubuntu, kernel 2.6.17-10-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd        /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title        Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd        /boot/initrd.img-2.6.17-10-generic
boot

title        Ubuntu, memtest86+ 
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Professional
root        (hd0,0) 
savedefault
makeactive
chainloader    +1

---

### Post by confused57 on 2007-02-27
You might want to try to change the entry for Windows from:
root (hd0,0)

to

rootnoverify (hd0,0)


sometimes this works, especially for XP.

---

### Post by moomintroll on 2007-02-27
That seemed to make things better - once! Got into XP once but now if I reboot or boot from cold we are back to seeing xp splash screen briefly before system reboots and asks if i want to boot in safe mode and then still doesnt load. 

any ideas would be gratefully recieved.

---

### Post by Foudre on 2007-02-27
well after changin the grub from the grub editor on boot, its only temp change, i had a similair problem way back when, i had to edit the grub file itself in linux, can't remember where its at, but thats what you need to change, but editing the grub around enough times can help you figure out what you need to change to what

---

### Post by moomintroll on 2007-02-27
One other thing I have noticed - if I boot in to Ubuntu and then restart I ca then boot in to XP - weird?
Ta!

---

### Post by confused57 on 2007-02-27
> **moomintroll said:**
> One other thing I have noticed - if I boot in to Ubuntu and then restart I ca then boot in to XP - weird?
Ta!

I don't know what's going on...one other thing you might try is to remove the line with "savedefault"...may not make a difference, but worth a try.

---

### Post by mahy on 2007-02-27
try removing the 'savedefault' line

---

### Post by moomintroll on 2007-02-28
Removed the 'savedefault' line and tried again -same thing - I can only boot into windows if I boot ubuntu and then restart into windows

---

### Post by moomintroll on 2007-03-01
Come on guys - dont make me go back to the dark side of microsoft - I want to make this work!

When I installed it xp first partition hda,0
                           Edgy 2nd partition hda,1
                           swap 3rd partition hda,2

the \ boot is in partiion 0

I also have another drive hdb

---

