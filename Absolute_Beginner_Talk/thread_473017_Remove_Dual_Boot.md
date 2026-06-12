---
title: "Remove Dual Boot"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by captlogic on 2007-06-13
I've got a dual boot system between xp & feisty.

I've copied the xp partition to a vm inside linux and so now I want to 'reclaim' the space from the xp partition and 're-assign' it to the home partition.


My question is, how?

I know I don't want to overwrite the MBR or grub, but I'm not sure how to erase the xp data. (I assume I need to reformat as the first partition is ntfs.) 

Please Help

Currently
/dev/sda1 - xp
/dev/sda2 - home
/dev/sda3 - extended partition
/dev/sda4 - swap
ddev/sda5 - /

(Do linux partitions need to be in any particular order?)

Thanks in advance

---

### Post by wreti on 2007-06-13
Your best bet is to download and burn gparted live onto a cd (iso). Then boot from the cd. It's a handy tool to have in your arsenal.:)

---

### Post by annda on 2007-06-13
i second that. the easiest way is to use gparted to delete sda1 and expand sda2.

personally, i've never had problems resizing partitions using gparted or any other linux tools but **do back up** all your important data just in case.

---

### Post by euler_fan on 2007-06-13
gparted is on the standard ubuntu live CD under system. If you want a more current version, I would do as the others suggested.

Good Luck.

---

### Post by captlogic on 2007-06-13
Thanks for all the help, I'll try this out tonight and let everyone now how it goes.


Ubuntu (Users!) Rock

---

### Post by captlogic on 2007-06-15
Almost there...

I've deleted the winxp partition and moved other partitions around but I'm getting GRUB error 17 at boot.

my setup is
/dev/sda1   /    boot flag set true
/dev/sda2   linux-swap
/dev/sda3  ext3 format, but not mounted to anything yet
/dev/sda4 /home

My fstab file

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
/dev/sda1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=98A8-38EC  /data           vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda4
/dev/sda4       /home           ext3    defaults        0       2

# /dev/sda2
/dev/sda2	 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

fdisk -l gives
```
ubuntu@ubuntu:/media/disk-1/etc$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1550    12450343+  83  Linux
/dev/sda2            1551        2171     4988182+  82  Linux swap / Solaris
/dev/sda3           15434       19457    32322780   83  Linux
/dev/sda4            5310       15433    81321030   83  Linux

```

and menu.lst says
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
# kopt=root=UUID=8ec7274e-4f20-4a50-9bfe-0e5df434e7d3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8ec7274e-4f20-4a50-9bfe-0e5df434e7d3 ro quiet splash nmi_watchdog=0
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8ec7274e-4f20-4a50-9bfe-0e5df434e7d3 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8ec7274e-4f20-4a50-9bfe-0e5df434e7d3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8ec7274e-4f20-4a50-9bfe-0e5df434e7d3 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title		Microsoft Windows XP Professional
#root		(hd0,0)
#savedefault
#makeactive
#chainloader	+1

```

I'm sure I'm missing something, probably obvious.

Thanks in advance.

---

### Post by confused57 on 2007-06-15
If you'll notice, your fstab mounting as /dev/sda1, whereas your kernel root is UUID...if you're getting a grub boot menu, highlight your Ubuntu entry, press "e", then change the kernel line to root=/dev/sda1, then press "b" to boot...this should get you into Ubuntu temporarily...if you prefer to use /dev/sda1, it can be made permanent by editing your /boot/grub/menu.lst.

It would probably be best to open a terminal, and run the command:
```
blkid
```

see if your /dev/sda1 UUID matches the entry in your menu.lst kernel line, then set up your fstab & kernel line with UUID's.

---

### Post by captlogic on 2007-06-15
Grub won't load so I can't fix from the menu, and when I run blkid from terminal I don't get any output.  Is that because I'm running from the liveCD?

OK, I edited my menu.lst file to point to /dev/sda1 instead of the UUID.

and I still get
grub loading stage 1.5
grub error 17

my menu.lst file now (just the relevant section-I think)

```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/sda1 ro quiet splash nmi_watchdog=0
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
```

---

### Post by confused57 on 2007-06-15
What I would suggest is to run a filesystem check on your root partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem)
if you scroll up a little, you'll see instructions for doing a filesystem check, using the gparted live cd:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

it's a small download(approx. 48 Mb), if you have access to another computer to burn a copy

You might also want to try the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's only a 5-7 Mb download & might be able to boot Ubuntu

Added:  It may not make any difference, but you might try reinstalling grub, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Here's a post by Herman of how to do a filesystem check with the Ubuntu live cd:
[http://ubuntuforums.org/showpost.php?p=2848047&postcount=2](http://ubuntuforums.org/showpost.php?p=2848047&postcount=2)

---

### Post by captlogic on 2007-06-15
Thanks, I'll give it a look!

---

### Post by captlogic on 2007-06-15
> **confused57 said:**
> What I would suggest is to run a filesystem check on your root partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem)
if you scroll up a little, you'll see instructions for doing a filesystem check, using the gparted live cd:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

it's a small download(approx. 48 Mb), if you have access to another computer to burn a copy

You might also want to try the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's only a 5-7 Mb download & might be able to boot Ubuntu

Added:  It may not make any difference, but you might try reinstalling grub, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Here's a post by Herman of how to do a filesystem check with the Ubuntu live cd:
[http://ubuntuforums.org/showpost.php?p=2848047&postcount=2](http://ubuntuforums.org/showpost.php?p=2848047&postcount=2)

filechecks were fine and reinstalling grub didn't help either.
So I said screw it, reinstalled.  Problem solved.

---

### Post by Songwind on 2007-06-15
If I don't have so much stuff to back up that it's a problem I always default to reinstalling.  It's just not that hard to get everything back the way you want it, with the repositories.

---

