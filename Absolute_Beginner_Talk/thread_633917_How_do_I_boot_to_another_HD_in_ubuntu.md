---
title: "How do I boot to another HD in ubuntu?"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by xeno1313 on 2007-12-07
I can't find an answer in any places and search hasn't turned anything up, so I'm just wondering how I can boot to Windows install that's on a seperate HD in Ubuntu..:confused:

---

### Post by PmDematagoda on 2007-12-07
Usually you can do that in [Virtual Box]("http://www.virtualbox.org/wiki/Downloads"), but whether you can do that to an already installed Windows is something I am not really sure about. If you do want to run Windows then you will have to reinstall anew on Virtual Box itself.

---

### Post by xeno1313 on 2007-12-07
I don't think I explained my question very well, I have 2 HDs, one with Ubuntu and the other with Win XP, I'm on the one with Ubuntu atm, and can't seem to find a way to boot back into the other HD with Win XP :P

---

### Post by PmDematagoda on 2007-12-07
Oh, that, sorry, I misinterpreted your question.

Post the result of:-
```

cat /boot/grub/menu.lst
```
and the result of:-
```

sudo fdisk -l

```

---

### Post by xeno1313 on 2007-12-07
menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# kopt=root=UUID=45e6a063-4f03-4862-8d08-063578fa317c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=45e6a063-4f03-4862-8d08-063578fa317c ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=45e6a063-4f03-4862-8d08-063578fa317c ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

fdisk
```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe25de25d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf14df440

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    7  HPFS/NTFS

```

thanks for the help ^^

---

### Post by PmDematagoda on 2007-12-07
You do not have the required entry to boot Windows.

1) Open up the menu.lst file for editing using:-
```

sudo gedit /boot/grub/menu.lst
```

2) Then go to last line and then enter this:-

```
title		Other operating systems:
root

title		Microsoft Windows XP
root		(hd1,0)
savedefault
makeactive
chainloader	+1

```

The entry:-
```

title		Other operating systems:
root
```

Is not essential, but just keeps the list clean.

3) After editing, save the file and then see if you can boot into Windows.

---

### Post by xeno1313 on 2007-12-07
Ah...it shows up in the menu okay, but when I select WinXP it hangs at "Starting Up..."

---

### Post by PmDematagoda on 2007-12-07
Post the result of:-

```
cat /boot/grub/device.map
```

---

### Post by xeno1313 on 2007-12-07
here ya go

```

(hd0)   /dev/sda
(hd1)   /dev/sdb

```

---

### Post by PmDematagoda on 2007-12-07
Ok, then change the entry to:-

```
title		Microsoft Windows XP
**root		(hd1,1)**
savedefault
makeactive
chainloader	+1
```

---

### Post by xeno1313 on 2007-12-07
boooo just gives me the error "Error 22 - No such partition or disk" :(

---

### Post by PmDematagoda on 2007-12-07
Then by rights the entry should be:-
```

title		Microsoft Windows XP
**root		(hd1,0)**
savedefault
makeactive
chainloader	+1
```

But if it does not work, then there might be something wrong with Windows itself.

You can give [Super GRUB]("http://supergrub.forjamari.linex.org/?section=download") a try to see if you can solve the problem using that.

---

