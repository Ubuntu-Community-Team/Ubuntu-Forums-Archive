---
title: "[SOLVED] Boot Properties"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by anderskitson on 2008-03-01
This is my Wynik.txt
> /dev/sda1: UUID="47C9-C73F" TYPE="vfat" 
/dev/sda2: TYPE="swap" UUID="594275c0-290c-440d-a35a-5525229a14f0" 
/dev/sda3: UUID="AAFCE7C13D2584C" TYPE="ntfs" 
/dev/sda4: UUID="66d830b6-1006-47f0-be9b-d192d425e576" TYPE="ext2" 
and this is my fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>      <options>                   <dump>  <pass>
proc            /proc           proc         defaults                    0       0

/dev/sdb4       /               ext2         defaults,errors=remount-ro  0       1

/dev/sda1       /media/sda1     ntfs         defaults                    0       0
/dev/sdb3       /media/sda3     ntfs         defaults,umask=007,gid=46   0       0

/dev/sdb2       none            swap         sw                          0       0
/dev/scd0       /media/cdrom0   udf,iso9660  user,noauto,exec            0       0
/dev/fd0        /media/floppy0  auto         rw,user,noauto,exec         0       0
I dont want to restart because i think something might go wrong, all I did was format an unallacated partition, but now windows wont boot, i think the boot is out of order now.

Please help

---

### Post by dstew on 2008-03-01
Please post the output of these commands:```
sudo fdisk -l
cat /boot/grub/menu.lst
```What is the error message that you get when you try to boot WIndows?

---

### Post by anderskitson on 2008-03-02
> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00066ff6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           30720       60801   241633665    b  W95 FAT32
/dev/sda2           10200       10321      979965   82  Linux swap / Solaris
/dev/sda3           10322       20520    81923467+   7  HPFS/NTFS
/dev/sda4   *       20521       30719    81923467+  83  Linux

Partition table entries are not in disk order

[QUOTE]Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x583f868b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14592   117210208+   7  HPFS/NTFS


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00066ff6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           30720       60801   241633665    b  W95 FAT32
/dev/sda2           10200       10321      979965   82  Linux swap / Solaris
/dev/sda3           10322       20520    81923467+   7  HPFS/NTFS
/dev/sda4   *       20521       30719    81923467+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x583f868b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14592   117210208+   7  HPFS/NTFS
anders@Anders:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=66d830b6-1006-47f0-be9b-d192d425e576 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=66d830b6-1006-47f0-be9b-d192d425e576 ro quiet 
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=66d830b6-1006-47f0-be9b-d192d425e576 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,3)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root





# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title           Microsoft Windows XP Home Edition
root            (hd0,2)
savedefault
makeactive
chainloader     +1
[/QUOTE]

I forgot to write down the error but is says im missing some sort of hal.dll file

---

### Post by dstew on 2008-03-02
> all I did was format an unallacated partitionYour disk order and partition tables have been changed. If you do this after you install, grub will get lost. It is easy to recover, but you have to do the steps carefully.

First, do you get the grub menu when you try to boot? What happens at the very beginning?

---

### Post by anderskitson on 2008-03-02
Ok well I get grub menu when i first boot up, ubuntu boots fine, but windoes gives me the error 
<windows root>\system32\hal.dll
Corrupt or missing

So im not sure what needs to be changes, im guessing a boot propertie in the boot.ini file dont know?
> [boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


---

### Post by dstew on 2008-03-02
I think you are right, that the problem is within Windows itself. [Here]("http://forums.microsoft.com/Communities/ShowPost.aspx?PostID=1050714&SiteID=6") is a Microsoft forum thread that deals with this problem. One way you can get this is if you are trying to boot the wrong partition in Windows, that is, the partition you are trying to boot is not really a bootable Windows system. 

I think this might be the case with your setup. I notice that your /dev/sda partition table has a big piece of unallocated space at the front of the drive (about 10,000 cylinders). Did you possibly have a Windows system there that might have gotten deleted? If so, grub might be fooled into setting up to boot /dev/sda3, grub name (hd0,2), which might not have an intact Windows system.

---

### Post by anderskitson on 2008-03-02
No that unallocated space, was a mistake i was trying to join it with another unallocated but i can't, and i can only have 4 main partitons. If i boot into windows i can expand the c drive into it, but it never was anything i can browse my windows files from linux it just wont boot, ill check that link out thanks

---

### Post by logos34 on 2008-03-02
Well I know one thing: if windows is sda3, boot.ini needs correcting:
> [boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(**[COLOR="Red"]3[/COLOR]**)\WINDOW S
[operating systems]
multi(0)disk(0)rdisk(0)partition(**[COLOR="Red"]3[/COLOR]**)\WINDOWS="Micro soft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

Although there may be another problem.

---

### Post by anderskitson on 2008-03-02
Actually i just did that, and it worked perfect. Thanks everyone for the help.

---

