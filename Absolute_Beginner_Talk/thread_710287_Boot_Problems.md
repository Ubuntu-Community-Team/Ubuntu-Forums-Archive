---
title: "Boot Problems"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by DestroyMicroshaft on 2008-02-28
OK here is my problem. Im not sure what happened but some time my system wont boot. Everything worked fine then all of a sudden about a week ago things went screwy. I wathed my system load, and when it get stuck, its the part of the boot process that says  "waiting for root file system". 

So I tried booting into recovery mode and this is what happens, when everything stops i get:

> check root=bootarg cat /proc/cmdline or missing modules, devices cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/ad936127-af7e-4c02-86d3-73fefb8ee0fc does not exist. Dropping to a shell!

That is the uuid for my root file system and id does exist, if I restart my pc 4 or 5 times itll boot
after the aove is stated I get a busy box 

Any ideas here? Greatly appreciate them!

---

### Post by taurus on 2008-02-28
Can you post the outputs of these commands?

```
sudo fdisk -l
ls -la /dev/disk/by-uuid
cat /etc/fstab
cat /boot/grub/menu.lst
```
Basically, you want to make sure that the UUID for / is the same.

---

### Post by DestroyMicroshaft on 2008-02-28
sure
> Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7702    61866283+   b  W95 FAT32
/dev/sda2            7703        7826      996030   82  Linux swap / Solaris
/dev/sda3   *        7827       19452    93385845   83  Linux

>    drwxr-xr-x 2 root root 100 2008-02-28 09:51 .
drwxr-xr-x 5 root root 100 2008-02-28 09:51 ..
lrwxrwxrwx 1 root root  10 2008-02-28 04:05 477D-08A8 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-02-28 04:05 acf9e0cc-cf6c-4732-81b9-19c9b7ddc860 -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-02-28 04:05 ad936127-af7e-4c02-86d3-73fefb8ee0fc -> ../../sda3
   
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ad936127-af7e-4c02-86d3-73fefb8ee0fc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=EC2C13E02C13A49C /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=acf9e0cc-cf6c-4732-81b9-19c9b7ddc860 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
# 46 is the USB group
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
##hiddenmenu

# Pretty colours
color black/red white/red

#A splash image for the menu
splashimage=(hd0,2)/boot/grub/splashimages/ubuntu-grub-fullcolor.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
#password --md5 $1$xTS7O$pzuqtq7B.u9yPJhqECk8Y/
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
# kopt=root=UUID=ad936127-af7e-4c02-86d3-73fefb8ee0fc ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
# lockalternative=true

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash vga=771

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
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=ad936127-af7e-4c02-86d3-73fefb8ee0fc ro splash vga=771
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
lock
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=ad936127-af7e-4c02-86d3-73fefb8ee0fc ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Mac OS X Leopard 
root            (hd0,3)
savedefault
makeactive
chainloader     +1
 

Thanx for the help!

---

### Post by taurus on 2008-02-28
What if you modify /boot/grub/menu.lst and make these

```

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=ad936127-af7e-4c02-86d3-73fefb8ee0fc ro splash vga=771
initrd /boot/initrd.img-2.6.22-14-generic
quiet

```
to look like these.

```

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,2)
**[COLOR="Blue"]#[/COLOR]**kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=ad936127-af7e-4c02-86d3-73fefb8ee0fc ro splash vga=771
[COLOR="Blue"]**kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/sda3 ro splash vga=771**[/COLOR]
initrd /boot/initrd.img-2.6.22-14-generic
quiet

```
Save it and reboot.

---

### Post by DestroyMicroshaft on 2008-02-28
Ill give it a try ty.

---

### Post by DestroyMicroshaft on 2008-02-28
Well it rebooted no problem, but it works sometimes and other times it doesnt so Ill try it for a few days and report back, thanx for the help.

---

