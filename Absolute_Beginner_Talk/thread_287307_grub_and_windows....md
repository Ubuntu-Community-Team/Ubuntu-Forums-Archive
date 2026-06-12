---
title: "grub and windows..."
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by threedguy on 2006-10-28
i can't get my windows xp installation to show up in grub.  I've tried everything i can find in these forums to try to fix the problem and so far, all have been unsucessful.  Here is the situation:  I have linux installed on my first hard drive, i have a storage hard drive set as my second hard drive, and I have windows xp on my third hard drive.  here is my fstab:

```
Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4669    37503711   83  Linux
/dev/hda2            4670        4870     1614532+   5  Extended
/dev/hda5            4670        4870     1614501   82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14595   117234306    7  HPFS/NTFS

Disk /dev/hdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        9729    78148161    7  HPFS/NTFS
```

and here is my menu.lst:

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
timeout		3

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
# kopt=root=/dev/hda1 ro

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

title Microsoft Windows XP
(hd2,0)
rootnoverify (hd2,0)
savedefault
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

```

I  have tried hd0,0 hd1,0 hd2,0 hd3,0 hd4,0 and hd5,0
hd3,0 and up return a disk not found error

hd1,0 and hd2,0 makes my floppy drive think really hard for a couple seconds and then it doesn't do anything

hd0,0 boots up ubuntu.

I can still access windows by editing my bios and booting up directly from that hard drive, but it would be nice if i could get grub to do it.

I tried the live cd grub restore idea, but i can't get past the partition setup; it really really really wants to reformat something.

I tried the super grub boot cd and haven't found anything that works on there.

surely it's just something simple i'm missing, if anyone has any idea how to fix this please post away.

---

### Post by Bachstelze on 2006-10-28
Here's what it should look like, or at least what it looks like in mine, and Windows boots just fine :)

```

title     Windows XP
root      whatever, in your case I think it should be (hd2,0)
makeactive
chainloader     +1

```

---

### Post by Herman on 2006-10-28
I have two suggestions to make here,

```
 ### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdd1

title         Microsoft Windows XP
map          (hd0) (hd2)
map          (hd2) (hd0)
rootnoverify (hd2,0)
savedefault
makeactive
chainloader +1
``` The first suggestion is to try using a pair of 'map' commands, Windows needs to be tricked into thinking it is number one on the first hard disk or it will sulk and refuse to boot. We can easily trick it with these 'map' commands.

Secondly, if you include an entry for any other operating system in your automagic kernels list, it will be deleted automagically when Ubuntu receives each kernel update. So make sure to add your Windows entry safely underneath the end of your automagic kernels list. It will be better off there.

I hope this will solve your problems, 
Regards, Herman :D

---

### Post by Bachstelze on 2006-10-28
Strange, my Windows is partition #2 and boots fine with just title/root/makeactive/chainloader...

---

### Post by bulldog on 2006-10-28
> **HymnToLife said:**
> Strange, my Windows is partition #2 and boots fine with just title/root/makeactive/chainloader...

It's not about partitions but fysical hdd's.

Windows like to be on the first hdd and by mapping the hdd's you can fool windows.

---

### Post by threedguy on 2006-10-28
> **Herman said:**
> I have two suggestions to make here,

```
 ### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdd1

title         Microsoft Windows XP
map          (hd0) (hd2)
map          (hd2) (hd0)
rootnoverify (hd2,0)
savedefault
makeactive
chainloader +1
``` The first suggestion is to try using a pair of 'map' commands, Windows needs to be tricked into thinking it is number one on the first hard disk or it will sulk and refuse to boot. We can easily trick it with these 'map' commands.

Secondly, if you include an entry for any other operating system in your automagic kernels list, it will be deleted automagically when Ubuntu receives each kernel update. So make sure to add your Windows entry safely underneath the end of your automagic kernels list. It will be better off there.

I hope this will solve your problems, 
Regards, Herman :D


That fixed it!!! I guess all the information i was finding dealt more with  a windows partition rather than an entirely seperate hard drive.  That was just almost as bad as installing my ATI graphics card...

---

### Post by Herman on 2006-10-28
Thank you for the feedback, I'm glad that worked. I think Grub is great! :D

Probably that will be all you'll ever need to learn about Grub, but if you have time and you would enjoy customizing your Grub menu, and maybe learning more about Grub, just click on my 'Grub Page' sig link, you might find something in there you'll enjoy, or just bookmark it for a rainy day.

Regards, Herman :D

---

