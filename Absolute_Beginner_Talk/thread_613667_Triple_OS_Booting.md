---
title: "Triple OS Booting"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by ziggy25 on 2007-11-15
This is what i have

IDE Master - disk1
IDE Slave - disk2

SATA Master - disk3

Disk1 has Windows XP installed on it.
Disk2 has Ubuntu 7.10 installed on it.
Disk3 has Fedora 8 installed on it.

Grub installed on Disk1 loads XP and Ubuntu
Grub installed on Disk 3 loads Fedora

When i installed Fedora (which was the last OS to be installed) it didnt show the other operating systems to add to Grub. Is this because they are on different disks? I now have to go into BIOS and select whether i need to boot from Disk1 or Disk3.

I would like to always boot from Disk1 and choose the operating system to load from the Grub instance on Disk 1. Is this possible?

Here are the disk paths on my computer and the contents of the grub configuration file on the ubuntu disk. 


Disk Drives and Partitions
```

ziggy@ziggy-ub:~$ sudo fdisk -l
[sudo] password for ziggy:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00370037

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          25      200781   83  Linux
/dev/sda2              26       30401   243995220   8e  Linux LVM

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3e4c3e4b

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/hdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44234423

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        6994    56179273+  83  Linux
/dev/hdb2            6995        7297     2433847+   5  Extended
/dev/hdb5            6995        7297     2433816   82  Linux swap / Solaris
ziggy@ziggy-ub:~$ cd /boot/grub
ziggy@ziggy-ub:/boot/grub$ 

```


/boot/grub/menu.lst
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

#This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

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
# kopt=root=UUID=3c7e2e56-9326-47d2-8822-de212a1ac363 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3c7e2e56-9326-47d2-8822-de212a1ac363 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3c7e2e56-9326-47d2-8822-de212a1ac363 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
#title		Microsoft Windows XP Professional
#root		(hd0,0)
#savedefault
#makeactive
#chainloader	+1


```

---

### Post by bulldog on 2007-11-15
Copy the boot part from the menu.lst which is on the Fedora hdd.
Put in the menu.lst from the first disk and voila.
Keep in mind,if you upgrade the fedora kernel,it will not automatically be changed,you have to do this yourself.

---

### Post by ziggy25 on 2007-11-15
> **bulldog said:**
> Copy the boot part from the menu.lst which is on the Fedora hdd.
Put in the menu.lst from the first disk and voila.
Keep in mind,if you upgrade the fedora kernel,it will not automatically be changed,you have to do this yourself.

Now why didnt i think of that :confused:

having said that.. i think the paths/names/mount point to the disks are different on Ubuntu and Fedora. Ill have to check this when i get back home.. 

Thanks

---

### Post by ziggy25 on 2007-11-16
Hi guys, 

I decided that i will use the grub installed with Fedora because it looks better than the one installed with the Ubuntu installation. 

I had a look at the Grub configuration file in with the Fedora installation and it looks different from the one i posted earlier. 

As you can see from the partitions list below, some of the disks are refered to as /dev/sd* rather than /dev/hda. i thought i could have just copied the definition from the Ubuntu grub to the Fedora grub but it didnt work. 

I managed to updated the Fedora grub to include the Ubuntu installation but i couldnt add the Windows installation. 

I also dont understand why the partitions are listed as sd* but the grub file refers to them as hd*. 

After i edited this version of grub it loaded Ubuntu from (hd2,0) but it couldnt load windows from (hd1,0). What do i need to do to include the windows installation. 

Here are the partitions and disks
```


[root@localhost ~]# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00370037

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          25      200781   83  Linux
/dev/sda2              26       30401   243995220   8e  Linux LVM

Disk /dev/dm-0: 247.7 GB, 247732371456 bytes
255 heads, 63 sectors/track, 30118 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 2080 MB, 2080374784 bytes
255 heads, 63 sectors/track, 252 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30307800

Disk /dev/dm-1 doesn't contain a valid partition table

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3e4c3e4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/sdc: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44234423

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        6994    56179273+  83  Linux
/dev/sdc2            6995        7297     2433847+   5  Extended
/dev/sdc5            6995        7297     2433816   82  Linux swap / Solaris
[root@localhost ~]# 


```

Here is the grub config for the Fedora installation in the Sata drive. 

```

#grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,0)
#          kernel /vmlinuz-version ro root=/dev/VolGroup00/LogVol00
#          initrd /initrd-version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,0)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.23.1-42.fc8)
	root (hd0,0)
	kernel /vmlinuz-2.6.23.1-42.fc8 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.23.1-42.fc8.img
title Other
	rootnoverify (hd1,0)
	chainloader +1

#Ubuntu
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3c7e2e56-9326-47d2-8822-de212a1ac363 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```

Here is what i tried to include the WIndows disk but it didnt work

```

title		Microsoft Windows XP Professional
root		(hd1,0)
makeactive
chainloader	+1

```

---

### Post by inaneframe on 2007-11-16
Life is too short to mess with GRUB and I reinstall my OS's too often to deal with it.

I bought one of [these]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817186004") and 2 extra enclosures, you could get just one extra enclosure for a rail since you only have 2 IDE drives.

Do you have a reason to use both Fedora and Ubuntu?  Not trying to be presumptuous because I use several hard drives to boot but mainly for testing, to see how the other distros are doing.

I have an EXT2 500GB IDE sitting internally for backup purposes that I always permanently define as /media/"whatever" during an install.  I would sit that SATA you have as an internal backup, use it across your OS's and be done with it.

If you REALLY need to use Windows use this so it can read that SATA EXT2 internal: [http://www.fs-driver.org/](http://www.fs-driver.org/)

I've been using it for almost 2 years and been very satisfied.  I set my 500 to "Z:\" when I need to use Windows inside of virtualbox for some god awful reason.

Just throwing this out as a suggestion.  If you are like me and constantly trying OS's than you might give it a try.

---

