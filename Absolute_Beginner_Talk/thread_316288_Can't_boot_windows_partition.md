---
title: "Can't boot windows partition"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by cutlerite on 2006-12-10
Okay, so I can't boot my windows partition.  It gets stuck immediately at "starting up"  I haven't been able to access windows since I installed ubuntu.  

Which isn't a big deal, because I enjoy ubuntu much better....but right now I really need to.

any suggestions?

---

### Post by aysiu on 2006-12-10
Not sure I can help, but someone else might be able to if you post the output of these terminal commands: ```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by gn2 on 2006-12-10
You should be able to get it running with "Super Grub Disk"

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by cutlerite on 2006-12-10
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15657   125764821    7  HPFS/NTFS
/dev/sda2           29282       30401     8988840    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3           15658       28928   106599307+  83  Linux
/dev/sda4           28929       29281     2835472+   5  Extended
/dev/sda5           28929       29281     2835441   82  Linux swap / Solaris

Partition table entries are not in disk order

that's what it says.   I had a helluva time trying to get the hard drive to partition, and that probably messed it up.

---

### Post by igknighted on 2006-12-10
I've had trouble with FAT 32 as well, that is probably the cause of the error shown, which is probably not a big deal.  Post the result of the other command Aysiu listed, that will tell us how the Ubuntu boot loader is trying to load windows.

---

### Post by cutlerite on 2006-12-10
Here it is:

> cat /boot/grub/menu.lst
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
# kopt=root=UUID=99dd3fcd-f584-4e1f-9e5b-d0c3c1dbd864 ro
# kopt_2_6=root=/dev/sda3 ro

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

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows XP Media Center Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows NT/2000/XP
root            (hd0,1)
savedefault
makeactive
chainloader     +1



---

### Post by cutlerite on 2006-12-10
any ideas?

---

### Post by mahy on 2006-12-10
maybe you should put there "rootnoverify" instead of "root" and remove "savedefault". That's what works for me.

---

### Post by maccam94 on 2006-12-13
Have the exact same problem here, still looking for a solution. Nothing like installing this for a client and then running into a really bad error...

---

