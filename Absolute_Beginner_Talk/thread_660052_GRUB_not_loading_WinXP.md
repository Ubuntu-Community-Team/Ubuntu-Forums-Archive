---
title: "GRUB not loading WinXP"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by ElGeneralo on 2008-01-06
I am new to Linux and managed to install Ubuntu 7.10 plus Grub. The problem is that now windows does not load. It either gives me an Error 13 - Invalid or unsupported executable format or it hangs at "Starting up...". I have tried all sorts of things but cannot figure this out. Need help, please.

Here is how my menu.lst looks like:

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
default		1

splashimage=(hd1,0)/boot/grub/WidescreenKubuntuBootSplash.xpm.gz  

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
# kopt=root=UUID=fa30b845-f544-4213-b860-1fd1bd48de19 ro

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

title		Linux Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fa30b845-f544-4213-b860-1fd1bd48de19 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

## title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
## root		(hd1,0)
## kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fa30b845-f544-4213-b860-1fd1bd48de19 ro single
## initrd		/boot/initrd.img-2.6.22-14-generic

## title		Ubuntu 7.10, memtest86+
## root		(hd1,0)
## kernel		/boot/memtest86+.bin
## quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

Here is how my device.map looks like:

(hd0)	/dev/sda
(hd1)	/dev/sdb

this is what fdisk shows:

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        5158    31664115    7  HPFS/NTFS
/dev/sda3            5159        6374     9767520   83  Linux
/dev/sda4            6375        6496      979965    5  Extended
/dev/sda5            6375        6496      979933+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14589   117186111    7  HPFS/NTFS
 
and this is how my boot.ini looks like:

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

Thanks

---

### Post by bumanie on 2008-01-06
I am no expert on grub, however, as no-one has answered your post, I will try and get something started.
Firstly I will point out that windows prefers to be on the first sector of the primary drive. Your fdisk indicates that windows in on slave drive - is this correct?
the other thing I think that has happened (from looking at your grub menu.lst) is that the drives have been reversed as far as grub sees them. By this I mean, grub is showing the primary drive with ubuntu as (hd1,0) when normally it should be (hd0,?) and the secondary windows drive as (hd0,0) when it normally would be (hd1,?).

---

### Post by houstonbofh on 2008-01-06
Windows needs to be the first partition, and it is not.  If you do not have data you need to save, I would reinstall from scratch clean.  However, if you need to "Save" Windows, you will need to boot the live CD and run gparted and remove all but the Windows partition, then slide it to the beginning.  Then boot a Windows CD that will allow you to "fdisk /mbr" to bot into Windows.  Clean it up, and then install Linux after Windows.

---

### Post by ElGeneralo on 2008-01-06
Thanks but I don't get it. My Bios views my hard drives as follows:

SATA Primary Drive is my 120 GB (this is where WinXP is installed and recognized in linux as sdb)
SATA Secondary NONE
Primary Master Drive is my 60 GB (this is where Linux is installed and is recognized in linux as sda
Primary Slave Drive NONE

So, in theory the WinXP hd should be hd0 and linux hd1, but device.map has them as hd0=linux and hd1=winXP. Could this be the problem?

---

### Post by jken146 on 2008-01-06
> /dev/sdb1 * 1 14589 117186111 7 HPFS/NTFS
According to this line in your output from **fstab -l**, XP is on (hd1,0) and not (hd0,0) as you have in your /boot/grub/menu.list -- try changing the entry to reflect this.

---

