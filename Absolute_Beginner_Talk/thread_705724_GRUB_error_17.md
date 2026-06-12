---
title: "GRUB error 17"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by Kdawkins on 2008-02-23
hey everyone,

I am brand new to the Linux OS family. Today I downloaded Ubuntu 7.10 (64-bit version) and installed it onto a new HD on my system. My goal was to be able to tri-boot between XP, Vista, and Ubuntu. I installed Ubuntu and after the re-boot I got a "error 17." I have 3 hard drives, one with XP, one with Vista, and one with Ubuntu.... I cannot boot past the GRUB error, so I am stuck using the CD live Ubuntu. 

I noticed in some other forums you guys usually ask for this so:


```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x91329132

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    19928159     9964048+   c  W95 FAT32 (LBA)
/dev/sda2   *    19928160   488375999   234223920    7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2066f466

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   586067264   293033601    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x69805a2a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   953023994   476511966   83  Linux
/dev/sdc2       953023995   976768064    11872035    5  Extended
/dev/sdc5       953024058   976768064    11872003+  82  Linux swap / Solaris

Disk /dev/sdd: 1030 MB, 1030750208 bytes
16 heads, 32 sectors/track, 3932 cylinders, total 2013184 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x943b7ded

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              32     2013183     1006576    e  W95 FAT16 (LBA)

```

---

### Post by Crooksey on 2008-02-23
Can you post..

```

/boot/grub/menu.lst
```

---

### Post by Kdawkins on 2008-02-23
when I try to do that I get:

ubuntu@ubuntu:~$ /boot/grub/menu.lst
bash: /boot/grub/menu.lst: No such file or directory

---

### Post by lolzlolz on 2008-02-23
it would appear somehow that your ubuntu partition got deleted or somehow grub got deleted off your hardrive, you may have to reinstall ubuntu to fix it although there might be some other way to get grub "back" on your hard drive ???

---

### Post by teryowen on 2008-02-23
nono...

Mount you sdc drive

so do this
mkdir /media/sdc1
sudo mount /dev/sdc1 /media/sdc1

then do
cat /media/sdc1/boot/grub/menu.lst

---

### Post by teryowen on 2008-02-23
But instead of what i mentioned above which was just to correct lolzlolz do the followin

in terminal:

sudo grub
root (sd2,0)
setup (sd2)
quit

now reboot your computer see if that works.

EDIT: By the way thank you for the sudo fdisk -lu  that is very helpful when trying to help others.

---

### Post by drs305 on 2008-02-23
If the above doesn't work, you might be able to salvage things with the SuperGrub CD. Here is a link:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Windows](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Windows)

Even though it says windows there is a lot of linux/ubuntu stuff as well.

---

### Post by piousp on 2008-02-23
Did you notice anything funny during the instalation?

---

### Post by Kdawkins on 2008-02-23
ok, I was able to get the menu.lst to show up. I changed the order in device.map to reflect the BIOS view of the hard drive order. 

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
# kopt=root=UUID=1652cde0-8a1b-420f-8527-27040996cf71 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=1652cde0-8a1b-420f-8527-27040996cf71 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=1652cde0-8a1b-420f-8527-27040996cf71 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd2,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1

root@ubuntu:/boot/grub# 


```

---

### Post by JoshuaRL on 2008-02-23
That seems to say that everything is loaded.  What's active on your Grub menu upon startup?

---

### Post by teryowen on 2008-02-23
run the commands:

sudo grub
root (sd2,0)
setup (sd2)
quit

---

