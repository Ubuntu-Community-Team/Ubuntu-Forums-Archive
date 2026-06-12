---
title: "Partitioning questions"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by asgard_command on 2007-10-19
A couple of things that have me currious if anyone can advise.

I have 100gb hard drive previously it was set up 10gb windows recovery partition a 45gb windows system partition and 45 for data. I wiped the recovery partition and used that to try out Feisty.
For Gutsy as I am using Ubuntu all the time and very little windows I wanted more space for Ubuntu so I backed up and deleted my windows data partition leaving just the one partition as NTFS.

After deleting this, Ubuntu Feisty failed to start. Why does deleting a windows ntfs partition affect the ubuntu install?

Secondly I now have the 10gb original ubuntu space going to waste. I had thought to just add this to the windows partition as it is next to it on the disc now but it won't let me change it in windows disc management. I assume as it is at the beginning of the disc it has the MBR on it. Does Grub also install on that partition? How can I make use of this space?

---

### Post by Pumalite on 2007-10-19
Post:
sudo fdisk -lu

---

### Post by tech9 on 2007-10-19
> **asgard_command said:**
> A couple of things that have me currious if anyone can advise.

I have 100gb hard drive previously it was set up 10gb windows recovery partition a 45gb windows system partition and 45 for data. I wiped the recovery partition and used that to try out Feisty.
For Gutsy as I am using Ubuntu all the time and very little windows I wanted more space for Ubuntu so I backed up and deleted my windows data partition leaving just the one partition as NTFS.

After deleting this, Ubuntu Feisty failed to start. Why does deleting a windows ntfs partition affect the ubuntu install?

Secondly I now have the 10gb original ubuntu space going to waste. I had thought to just add this to the windows partition as it is next to it on the disc now but it won't let me change it in windows disc management. I assume as it is at the beginning of the disc it has the MBR on it. Does Grub also install on that partition? How can I make use of this space?

use the liveCD to create another data partition ext2 or 3

---

### Post by asgard_command on 2007-10-19
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7230649d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       110430810   129949784     9759487+  83  Linux
/dev/sda2       191462670   195366464     1951897+  82  Linux swap / Solaris
/dev/sda3   *    19531776   110420527    45444376    7  HPFS/NTFS
/dev/sda4       129949785   191462669    30756442+   5  Extended
/dev/sda5       129949848   191462669    30756411   83  Linux

---

### Post by Pumalite on 2007-10-19
Post:
cat /boot/grub/menu.lst

---

### Post by asgard_command on 2007-10-19
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
# kopt=root=UUID=d0b13490-d9cf-4924-a169-2be43c1617a9 ro

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
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=d0b13490-d9cf-4924-a169-2be43c1617a9 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=d0b13490-d9cf-4924-a169-2be43c1617a9 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title           Windows Vista/Longhorn (loader)
root            (hd0,2)
savedefault
makeactive
chainloader     +1

---

