---
title: "Windows won't load"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by kendrick on 2007-05-26
I succesfully installed ubuntu and it is my first version of linux however something seems to have gone wrong, when trying to load windows xp this shows up: 
```
Booting 'Microsoft Windows XP Professional'

root (hd0,0)
Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

_
```

and then it sits there and acts as if it is done. Any ideas as to what is going on?

---

### Post by drowner on 2007-05-26
open a terminal and post the output of

```
sudo fdisk -l

```
and

```
cat /boot/grub/menu.lst

```

The first command tells us which partitions and drives can be seen on your computer, the second command displays the contents of menu.lst, a file used by GRUB to boot the various operating systems on your computer.

---

### Post by kendrick on 2007-05-26
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       12732   102269758+   7  HPFS/NTFS
/dev/hda2           12733       14513    14305882+  83  Linux
/dev/hda3           14514       14593      642600    5  Extended
/dev/hda5           14514       14593      642568+  82  Linux swap / Solaris


=======================================================


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
#color white/blue

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
# kopt=root=/dev/hda2 ro

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

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,1)
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

### Post by drowner on 2007-05-26
I found the answer, using this brand new thing i just found out about... google.com. It's brilliant ;)

[http://support.novell.com/techcenter/sdb/en/2004/05/fhassel_windows_not_booting91.html](http://support.novell.com/techcenter/sdb/en/2004/05/fhassel_windows_not_booting91.html)

---

### Post by drowner on 2007-05-26
> **drowner said:**
> I found the answer, using this brand new thing i just found out about... google.com. It's brilliant ;)

[http://support.novell.com/techcenter/sdb/en/2004/05/fhassel_windows_not_booting91.html](http://support.novell.com/techcenter/sdb/en/2004/05/fhassel_windows_not_booting91.html)

I have no idea if that SuSE thing will work, but it seems it migh
I'll google an ubuntu specific option

---

### Post by drowner on 2007-05-26
There are heaps out there!

---

### Post by kendrick on 2007-05-26
I can't figure out what to do, I can't get an ftp connection with suse and I have no idea what they are talking about in the BIOS, do you have any ubuntu specific information. I see lots of threads with this problem but no solutions.

---

### Post by drowner on 2007-05-26
> **kendrick said:**
> I can't figure out what to do, I can't get an ftp connection with suse and I have no idea what they are talking about in the BIOS, do you have any ubuntu specific information. I see lots of threads with this problem but no solutions.

No, I don't.

i just googled it, just like you.

I don't know enough about it confidently make a recommendation, but it is a known bug

If another user has successfully circumvented this problem, feel free to jump in

Have you ever edited your BIOS? Write down what they say, press a few buttons when you first turn on your computer  (typically F1, F2, DEL, ESC....)- your computer may tell you the right one - and have a look around, see if you can find what they are talking about.

---

