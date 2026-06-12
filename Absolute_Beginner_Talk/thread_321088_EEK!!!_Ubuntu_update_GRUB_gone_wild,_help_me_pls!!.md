---
title: "EEK!!! Ubuntu update GRUB gone wild, help me pls!!"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by gingerj on 2006-12-18
Hi ya all,

I installed Ubuntu for the very first time on friday or thurs (many thanks to those on the forum that helped), after reading chp 4 of the official book. 

I finally started to try and 'use' Ubuntu, so I noticed in the notification area that I had 204 updates. As I think the book comes with 6.06, so plenty of updates to be had.

I've restarted my machine and now GRUB has lost all my windows boot information.

I've got my original GRUB menu.lst file here:
[http://www.ubuntuforums.org/showthread.php?t=318664](http://www.ubuntuforums.org/showthread.php?t=318664)

Can I merge a couple of statements to get GRUB to see my windows partition and put the windows bit at the top again. Or has the update done something far more serious??


here's my new GRUB file:
> 
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

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

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


Many thanks and cheers in advance!

---

### Post by Rippey on 2006-12-18
look is there is a file called menu.lst~ in the grub folder, this is a backup of menu.lst
find the windows part in there and copy it to your current menu.lst

---

### Post by confused57 on 2006-12-18
Rippey's method should work...but you could also open your /boot/grub/menu.lst, then copy & paste your Windows entries that you have listed in your other thread.

Do you have 2 different Windows OS installed?  If you know which entry you use to boot Windows, you could paste it above the line:
#BEGIN AUTOMAGIC KERNEL LIST

similar to what's described here:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)
The Windows entry in the above link is for Windows on a 2nd hard drive, so don't use that one.

If you have a kernel update & subsequent update-grub, Windows will still be the first OS automatically booted by grub if you place it as I've mentioned...least it's an option.

---

### Post by gingerj on 2006-12-18
Yeah I fixed the menu.lst file by copy and pasting between my old one (from my previous thread) and the new one, I had no backup copy.

Although can I ask does this happen every time I update my kernal, or was it that in the 204 updates one was a GRUB one and when a new GRUB update occurs is does some weird stuff to your menu.lst file. Or both? I'm a bit confused how the file was re-written without me being asked, especially such a vital file the one that controls your boxes master boot record.

---

### Post by confused57 on 2006-12-18
> **gingerj said:**
> Yeah I fixed the menu.lst file by copy and pasting between my old one (from my previous thread) and the new one, I had no backup copy.

Although can I ask does this happen every time I update my kernal, or was it that in the 204 updates one was a GRUB one and when a new GRUB update occurs is does some weird stuff to your menu.lst file. Or both? I'm a bit confused how the file was re-written without me being asked, especially such a vital file the one that controls your boxes master boot record.

This link explains what happens when a kernel is updated:
[http://users.bigpond.net.au/hermanzone/p15.htm#DEBIAN_AUTOMAGIC_KERNELS_LIST](http://users.bigpond.net.au/hermanzone/p15.htm#DEBIAN_AUTOMAGIC_KERNELS_LIST)

---

