---
title: "won't boot from floppy: error 15 file not found"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by leavingOS2 on 2007-01-11
I've completed my first install of Ubuntu (my first linux) except for attempting to add the IBM Boot Manager (to load OS/2 onto my Grub menu.  I figured I would try to make a grub boot floppy first, and try adding it there, before messing with my hd, but I get the "error 15 file not found" message" when attempting to boot from the floppy.

Any assistance in getting the boot floppy working would be appreciated.

To make the boot floppy, I followed instructions from here: [https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy)

When choosing ubuntu boot floppy menu, I get this:
"root (hd0,4)
filesystem type is ext2fs, partition type os 0x83
kernel /boot vmlinz-2.6.15-26-386 root= /dev/sda5 ro quiet splash
[Linux-bzImage, setup 0x1e00 size=0x15787d]
initrd /boot/initrd.img-2.6.15-26-386
[Linux-initrd @ 0x1f941000, 0xae411 bytes]
savedefault

error 15 = file not found

press any key to continue"

Here is my fdisk -l results:
"Disk /dev/sda: 73.4 GB, 73407865856 bytes
255 heads, 63 sectors/track, 8924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1        8001    a  OS/2 Boot Manager
/dev/sda2   *           2         190     1518142+   b  W95 FAT32
/dev/sda3             191        8924    70155855    5  Extended
/dev/sda5   *         191         895     5662881   83  Linux
/dev/sda6             896        1021     1012063+   7  HPFS/NTFS
/dev/sda7   *        1022        1276     2048256   82  Linux swap / Solaris
/dev/sda8   *        1277        3827    20490876   83  Linux
/dev/sda9   *        3828        4082     2048256    7  HPFS/NTFS
/dev/sda10  *        4083        6375    18418491    b  W95 FAT32
/dev/sda11  *        6376        8924    20474811    7  HPFS/NTFS

Disk /dev/sdb: 18.3 GB, 18351959040 bytes
255 heads, 63 sectors/track, 2231 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2231    17920476    7  HPFS/NTFS

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       36481   293033601    7  HPFS/NTFS"

Here is my cat menu.lst results:
"# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=/dev/sda5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda5 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda5 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,4)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader     +1"

---

### Post by leavingOS2 on 2007-01-11
Well I got it to work, but I don't know if it is a sound solution:

I remmed the savedefault command.

Can this cause any problems?

---

