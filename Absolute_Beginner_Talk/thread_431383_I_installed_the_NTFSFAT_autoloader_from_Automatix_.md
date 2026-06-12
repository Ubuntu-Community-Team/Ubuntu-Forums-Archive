---
title: "I installed the NTFS/FAT autoloader from Automatix and now I can't boot to Windows!"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by willz06jw on 2007-05-03
Thanks for the help, I am about to explode since I have some things that are in XP that I need for finals next week.  

I installed the NTFS/FAT hard drive autoloader with Automatix and now I can't boot to Windows XP.  I saw another post about having trouble booting and you needed the menu and fdisk output. 


Let me give you the output of my menu.lst and fdisk -l commands:

fdisk -l
```
Disk /dev/sda: 200.0 GB, 200000000000 bytes
255 heads, 63 sectors/track, 24315 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       16708    31808700    f  W95 Ext'd (LBA)
/dev/sda5           12749       16708    31808668+   b  W95 FAT32

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4787    38451546   83  Linux
/dev/sdb2            4788        4998     1694857+   5  Extended
/dev/sdb5            4788        4998     1694826   82  Linux swap / Solaris
```


menu.lst:
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
# kopt=root=UUID=1af725f3-6d57-4f0f-b84b-e0e2faa673f9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=1af725f3-6d57-4f0f-b84b-e0e2faa673f9 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=1af725f3-6d57-4f0f-b84b-e0e2faa673f9 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

title           Microsoft Windows XP Media Center
root            (hd0,0)
savedefault
makeactive
chanloader +1
```



I wonder what the problem is!

Thanks for you time and help looking this over,
Will from Texas

---

### Post by STREETURCHINE on 2007-05-03
go to the automatix forums and post the problem there and arnieboy will sort it out for you

there is a link in my signature for the forums

if there is a problem it will help them sort it out as well

---

### Post by willz06jw on 2007-05-03
It was not Automatix that cause the problem, it was me.  I had chanloader +1 instead of chainloader +1 in the menu.lst file.

I fixed that and now it works perfectly.

Arnieboy and Automatix rock on support
:guitar: 

Will from Texas

---

### Post by STREETURCHINE on 2007-05-03
i am glad you fixed it,
i was not saying that automatix caused your problem,

but i knew arnieboy could sort it out,even if it wasnt anything to do with automatix, he will still help:)

---

