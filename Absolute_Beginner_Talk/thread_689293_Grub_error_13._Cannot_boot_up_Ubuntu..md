---
title: "Grub error 13. Cannot boot up Ubuntu."
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by MathsDude on 2008-02-06
I recently updated the Kernel for Ubuntu and now for some reason I cannot boot up Ubuntu. All other posts were concerning about Windows, but with me its the other way around.
When I do try to boot up Ubuntu I get the error message error 13.

Menu.lst:

gfxmenu /boot/grub/message.gulliver

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=11068223-bc3d-42cd-81a8-841a964b7942 ro

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
# defoptions=quiet splash vga=792

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

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=11068223-bc3d-42cd-81a8-841a964b7942 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
boot

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=11068223-bc3d-42cd-81a8-841a964b7942 ro single
initrd		/boot/initrd.img-2.6.22-14-generic
boot

title		Ubuntu 7.10, kernel memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by bwtranch on 2008-02-06
title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=11068223-bc3d-42cd-81a8-841a964b7942 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
boot

I think if you update these lines (to your current version) it should work.

---

### Post by bwtranch on 2008-02-06
Don't forget to mount

---

### Post by MathsDude on 2008-02-06
Thanks for the quick reply. 
Problem is I have no idea what the latest version is after going through the filesystem folders.
Could you elaborate more as to what I have to do please?

I guess these problems always show how little we do know about Linux

---

### Post by MathsDude on 2008-02-06
Ok by the looks of it I have managed to resolve the problem but in a very dirty manner...
By the looks of it the kernel update just updated empty files or not complete files when I compared the files in boot folder with a friend of mine who's kernel update worked fine.
The filesystem must of have been corrupted so I run fsck manually to fix the filesystem. In the end I had to copy the boot files from my friend which actually fixed the problem...

Not quite a good way but it did work for me. 
But I don't think this is case closed. I still would like to know what caused this problem in the first place. the update? Maybe something in one of the partitions got altered?

---

### Post by dstew on 2008-02-06
It seems from the grub error that the new kernel image was somehow corrupted during the update process. Maybe this was just bad luck, maybe the file transfer went astray somehow, and it won't happen again.

---

### Post by bwtranch on 2008-02-06
Re #6

It seems that that is what happened. I wouldn't feel highly confident that it won't happen again though. These things tend to rear their ugly head again. Usually at the worst time. I would backup and do a clean install from a CD that I did a checksum on.  Just backup what is important like /home or whatever. I do think the kernel needs a re-compile. Just my two cents. Good Luck!

---

### Post by bwtranch on 2008-02-06
Oh yeah, one more thing. (if anybody is still reading this one, besides me) There is a great list of terminal commands in The Linux Commands Line List v1.2. (I would give you the URL, but they didn't put it on there, but you can Google) Print it out and put it by the toliet (makes for great reading). Another place for good docs about Linux (and those are hard to come by) is [www.gentoo.org](www.gentoo.org)

Someone once said (I can't remember who) that documentation is like sex, when it is good, it is very, very good. But, when it is bad, it is still better than nothing.:)

---

