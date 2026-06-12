---
title: "[SOLVED] Configure Grub"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by TheNatealator on 2008-01-22
So, I installed Ubuntu a few days ago, and finally got internet today (long story) and downloaded 185 critical and recommended updates and restarted my computer.  Unfortunately, Grub has forgotten I dual boot WinXP and Ubuntu!!!! I know it's there, I can see the partition from Ubuntu. The Windows information is simply not in /boot/grub/menu.lst

How do I find my Windows kernel information to put into /boot/grub/menu.lst ?

Thanks

---

### Post by wolfen69 on 2008-01-22
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by tojge on 2008-01-22
Could you paste the contents of your menu.lst file?

Or, the link above :-) even better

---

### Post by philinux on 2008-01-22
This is the bit in mine

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Windows 
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

---

### Post by TheNatealator on 2008-01-22
Followed the link, reinstalled grub, but menu.lst still shows the following:

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
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
# kopt=root=UUID=7a6e89c7-e8d6-48e1-811c-643b968a0697 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7a6e89c7-e8d6-48e1-811c-643b968a0697 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7a6e89c7-e8d6-48e1-811c-643b968a0697 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Still no windows. :(

---

### Post by philinux on 2008-01-22
Post the output of

sudo fdisk -l

thats a lower case L

---

### Post by tojge on 2008-01-22
Can you do ```
sudo fdisk -l
```

Edit: Geez, I am slow tonight... :-D

---

### Post by TheNatealator on 2008-01-23
As you might guess, Windows is on sda2.

```
nate@nate-laptop:~$ sudo fdisk -l
[sudo] password for nate:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2   *          10        7862    63079222+   7  HPFS/NTFS
/dev/sda3            9294        9729     3502170   db  CP/M / CTOS / ...
/dev/sda4            7863        9293    11494507+   5  Extended
/dev/sda5            9051        9293     1951897+  82  Linux swap / Solaris
/dev/sda6            7863        9049     9534514+  83  Linux

Partition table entries are not in disk order
```

---

### Post by tojge on 2008-01-23
Well, in that case, try appending the following at the end of your menu.lst, after ### END DEBIAN AUTOMAGIC KERNELS LIST
```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

title           Microsoft Windows XP Professional //or whatever, your choice
root            (hd0,1)
savedefault
makeactive
chainloader     +1
```

---

### Post by TheNatealator on 2008-01-23
Excellent. I'm now in windows, although I didn't do exactly what you said. Instead, I put the Windows stuff above the Automagic kernels, because I would like XP to be the first option. Will that cause any problems for me in the future?

---

### Post by tojge on 2008-01-23
I don't think it will, putting the "other operating systems" option after the Debian/Linux ones is just customary, but by no means obligatory... If I wanted Win to be the default booting option, I'd probably edit the **default grub root device** in menu.lst, but I guess your way works as well :-)

---

### Post by TheNatealator on 2008-01-23
In which case, Ubuntu would still be first in the list, but it would start out with Windows selected?

---

### Post by tojge on 2008-01-23
In which case it would boot Windows if you just leave it be, that is, do not press any key for the preset amount of time, defined under **timeout sec** value

---

### Post by TheNatealator on 2008-01-23
Excellent. Thanks for all the help.

---

### Post by tojge on 2008-01-23
You're welcome, glad to be of assistance. Anyway, if you want to go with that, look for the entry named **default grub root device** in menu.lst, you should see something like:
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)
```

Now, uncomment the last line (that is, remove the **#** character at the beginning), and change the value to represent your Win boot device, in your case (hd0,1), so it should read
```
## default grub root device
## e.g. groot=(hd0,0)
groot=(hd0,1)
```
And that's pretty much it :-)

---

### Post by -1nverse on 2008-01-24
Oops.... :oops:

---

