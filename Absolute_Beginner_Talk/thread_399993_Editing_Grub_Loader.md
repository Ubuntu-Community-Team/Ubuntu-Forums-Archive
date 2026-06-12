---
title: "Editing Grub Loader"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by brennydoogles on 2007-04-03
I recently re-installed ubuntu so that I could give it more hard drive space, and I am now triple booting with Windows XP, and two separate installations of Ubuntu. In order to make my booting easier, I would like to remove the old installation from the Grub loader, as I will eventually be reclaiming that space for storage. My question is, what would be the best way to remove the extra options without causing the computer to not boot properly?? I would really like to edit the loader in such a way as to give me only two options, Ubuntu and Windows, but i know that this can cause problems when updating the kernel. Would I be able to do this by commenting out certain parts of menu.lst until time to update the kernel?? Here is a copy of my menu.lst 

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
timeout		30

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
# kopt=root=UUID=6f7e9e85-2804-4047-90c3-7c283e15eb6a ro
# kopt_2_6=root=/dev/hdb1 ro

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

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
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
# on /dev/hda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda6.
title		Ubuntu, kernel 2.6.17-11-generic (on /dev/hda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda6 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda6.
title		Ubuntu, kernel 2.6.17-11-generic (recovery mode) (on /dev/hda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda6 ro single 
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda6.
title		Ubuntu, kernel 2.6.17-10-generic (on /dev/hda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda6.
title		Ubuntu, kernel 2.6.17-10-generic (recovery mode) (on /dev/hda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro single 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda6.
title		Ubuntu, memtest86+ (on /dev/hda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot


```

and here is a copy of my proposed fix:

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
timeout		30

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
# kopt=root=UUID=6f7e9e85-2804-4047-90c3-7c283e15eb6a ro
# kopt_2_6=root=/dev/hdb1 ro

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

title		[COLOR="Red"]Ubuntu[/COLOR]
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

#title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hdb1 ro single
#initrd		/boot/initrd.img-2.6.17-11-generic
#boot

#title		Ubuntu, kernel 2.6.17-10-generic
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
#initrd		/boot/initrd.img-2.6.17-10-generic
#quiet
#savedefault
#boot

#title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
#initrd		/boot/initrd.img-2.6.17-10-generic
#boot

#title		Ubuntu, memtest86+
#root		(hd1,0)
#kernel		/boot/memtest86+.bin
#quiet
#boot

### END DEBIAN AUTOMAGIC KERNELS LIST




# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		[COLOR="Red"]Windows[/COLOR]
root		(hd0,1)
savedefault
makeactive
chainloader	+1

[CENTER][COLOR="Red"]Everything from here down would be deleted.[/COLOR][/CENTER]


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda6.
title		Ubuntu, kernel 2.6.17-11-generic (on /dev/hda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda6 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda6.
title		Ubuntu, kernel 2.6.17-11-generic (recovery mode) (on /dev/hda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda6 ro single 
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda6.
title		Ubuntu, kernel 2.6.17-10-generic (on /dev/hda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda6.
title		Ubuntu, kernel 2.6.17-10-generic (recovery mode) (on /dev/hda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro single 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda6.
title		Ubuntu, memtest86+ (on /dev/hda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot


```

How does that look? Any help would be greatly appreciated.

---

### Post by confused57 on 2007-04-03
Since your newer Ubuntu install is on hdb, then that's the grub  that's installed on your hd0 mbr...you "shouldn't" have any problems booting with how you propose to edit your menu.lst.

You might want to boot into your Ubuntu install on hdb1, open your /etc/fstab, and comment out the mountpoint for /dev/hda6.  If you don't booting up may give you an error after you delete the partition.
Open a terminal and post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

If you can post this, then someone should be able to tell you if what you're planning will work without any problems.

Before you delete any partitions, you might want to burn a copy of the Super Grub Disk(500 kb download):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

You can always reinstall grub with the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Wouldn't hurt to backup your menu.lst, before editing:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

Added:  To answer your question, just deleting these entries in your menu.lst as you propose shouldn't affect booting your computer, since the grub you're using is your newer install.

---

### Post by brennydoogles on 2007-04-05
Sweet. i made the proposed changes this morning, and the computer boots beautifully. I now only have two boot options... "Windows" and "Ubuntu" . Much easier than the 7 or 8 I had before. Thanks for the help!!

---

