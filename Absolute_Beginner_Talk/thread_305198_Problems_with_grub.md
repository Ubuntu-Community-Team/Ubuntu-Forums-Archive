---
title: "Problems with grub"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by OMRebel on 2006-11-22
Hey guys.  I'm having a problem.  I just replaced my IDE drive with a larger drive, and installed Ubuntu on it.  I have a SATA drive that has Windows XP on it.  However, I can't boot into Windows XP now for some reason.  Here is my grub:

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
# kopt=root=UUID=11d8f387-0a72-45ac-a6ea-9aa69ad9f659 ro
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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

Previously, I would just specify hd0 in the grub menu when I had the other IDE in that had Ubuntu on it, and it would boot into Windows, but not now.

What can I do to get this corrected, as I must keep Win XP for work?  Thanks everyone.

---

### Post by Afishionado on 2006-11-22
A SATA hard drive should be /dev/sda0 instead of /dev/hda0.

Another of Linux's idiosyncracies. :-)

---

### Post by OMRebel on 2006-11-22
Thanks.  I'll give that a shot.

---

### Post by OMRebel on 2006-11-22
Nope.  I get a parsing error when I try to change the drive names.  Is there anything I can look up to find out exactly what it needs to be?

---

### Post by OMRebel on 2006-11-23
I did a sudo fdisk -l and got this:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9541    76638051   83  Linux
/dev/hda2            9542        9729     1510110    5  Extended
/dev/hda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS


This is where I'm confused.  In grub, I use hd1 to boot into Ubuntu.  Yet, the names showing here would be hda1, etc..  So, do I use sd1, or is there a way to tell what name the bootloader will actually be looking for?

---

### Post by confused57 on 2006-11-23
You can try removing the 2 lines with map in your Windows entry...then try to boot Windows.

What you can do is highlight the Windows entry in grub, press "e" for edit, remove the 2 lines with "map", then try to boot.   This change is only temporary, but if Windows boots, you can make it permanent in your /boot/grub/menu.lst.

---

### Post by CatKiller on 2006-11-23
I don't think it would be sd1. GRUB doesn't distinguish between interface types, as I understand it. It's either a floppy drive starting at **fd0** or it's something else starting at **hd0**. I don't know for sure how to find out how each drive is numbered (I've not had to configure GRUB) but I vaguely recall something about **locate** from a **grub** prompt to find a known file.

Hope this helps.

---

### Post by confused57 on 2006-11-23
> **confused57 said:**
> You can try removing the 2 lines with map in your Windows entry...then try to boot Windows.

What you can do is highlight the Windows entry in grub, press "e" for edit, remove the 2 lines with "map", then try to boot.   This change is only temporary, but if Windows boots, you can make it permanent in your /boot/grub/menu.lst.

This site has some excellent information about grub:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Grub's designation for hard drives doesn't differentiate between SATA and IDE drives.
hd0 is the first hard drive in grub, whether it is sda or hda.
(hd0,0) in grub is the same as sda1(or hda1)
(hd0,1)  "   "                 sda2(or hda2)
(hd1,0) is the 1st partition on 2nd hd in grub, in Ubuntu it's sdb1(or hdb1)

Edit: Don't know how I managed to quote myself, forum has been rather slow and unpredictable for me lately.

---

### Post by OMRebel on 2006-11-23
@Confused57 

That worked perfectly!  

Thanks for everyone's help in this thread.

---

### Post by OMRebel on 2006-11-23
One more question - how would I mount my Windows drive so I can copy some files over?  Thanks.

---

### Post by confused57 on 2006-11-23
See this link:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

You can mount your Windows temporarily, using the live cd method, but actually mounting it in your Ubuntu install...or you mount permanently, by adding an entry to your /etc/fstab, as described in the link.

---

