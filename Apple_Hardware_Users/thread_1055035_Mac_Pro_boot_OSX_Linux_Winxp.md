---
title: "Mac Pro boot OSX Linux Winxp"
date: 2009-01-30
forum: Apple Hardware Users
---

### Post by yepper on 2009-01-30
HI, 

Im all out of searching and doing... Here's my situation, would appreciate any help. 

I have a 2006 Mac Pro 2.66 quad. 
Bay 1 OSX 10.5.5
Bay 2 Linux Mint x64
Bay 3 Winxp x64

reFit is installed

I wish i could drop windows, but to many programs i have to use on it. And linux is just much faster at running a few of them. Plus I like it better. 

Anyway, my Linux wont boot. Error 17 after selecting Linux in the GRUB menu. Windows XP x64 will boot fine and Im booting thru GRUB so that I can use the stage1 file to access  my 5 and 6 SATA ports. So OSX = fine, Linux = Error 15 , and WinXp x64 =Fine.

Ive seen that the problem could be the device.map , because when I do an fdisk -l the drives show up as 

sda osx
sdb winxp
sdc linux

device.map 
hd0 sda
hd1 sdb
hd2 sdc

Seems like linux should be sdb or at leats hd1 , but when I do a grub , find /boot/grub/stage1 it reports (hd2,0). Which seems correct, but still think it should be hd1. Anyway I tried switching the mapping and didnt seem to notice any change and was still receiving an Error 17.

I tried update-grub and grub-install , but neither have helped. I cant remember if I was in chroot or not. And now Im talking out my butt because I dont know much about Linux. I just try to piece-meal together what I can from the forums. 

Any Ideas would be greatly appreciated. Ill come back and post my device.map  menu.lst and whatever the lovely person that helps would like to see.

Oh, I tried SuperGrub.. but it wont get past the ... .loading Stage2 phase. And reFit says Im synched

device map
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

sudo grub
Probing devices to guess BIOS drives. This may take a long time.

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd2,0)
grub> root (hd2,0)
root (hd2,0)
grub> setup (hd2)
setup (hd2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd2)"...  19 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd2) (hd2)1+19 p (hd2,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.


menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/default.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sdc1 ro

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
##      altoptions=(single-user) single
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

title		Linux Mint 6 x64 Edition, kernel 2.6.27-7-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sdc1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Linux Mint 6 x64 Edition, kernel 2.6.27-7-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sdc1 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Linux Mint 6 x64 Edition, kernel Last successful boot
root		(hd2,0)
kernel		/boot/last-good-boot/vmlinuz root=/dev/sdc1 ro quiet splash  last-good-boot
quiet

title		Linux Mint 6 x64 Edition, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

fdisk -l 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36c048c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      204819+  ee  GPT
/dev/sda2              26       30385   243862672   af  Unknown
/dev/sda3           30385       30402      131072   c0  Unknown

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a73a293

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19a719a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9328    74921875+  83  Linux
/dev/sdc2            9328        9730     3228835   82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8dcb0627

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       60801   488384001   af  Unknown


Parted

 sudo parted /dev/sdc print
Model: ATA ST380815AS (scsi)
Disk /dev/sdc: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      17.4kB  76.7GB  76.7GB  primary  ext3         boot 
 2      76.7GB  80.0GB  3306MB  primary  linux-swap        

sudo parted /dev/sda print
Model: ATA ST3250824AS P (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name                          Flags  
 1      20.5kB  210MB  210MB  fat32        EFI System Partition          boot   
 2      210MB   250GB  250GB  hfs+         Untitled                             
 3      250GB   250GB  134MB  ntfs         Microsoft reserved partition  msftres

sudo parted /dev/sdb print
Model: ATA MAXTOR STM316081 (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system  Name  Flags
 1      17.4kB  154GB  154GB   ext3               boot 
 2      154GB   160GB  6040MB

---

### Post by cyberdork33 on 2009-01-30
when you have Linux installed on a completely different hard drive, you can have some weird issues... 

See:
[http://wiki.debian.org/DebianOnIntelMacPro#line-187](http://wiki.debian.org/DebianOnIntelMacPro#line-187)

---

### Post by yepper on 2009-01-31
hrm, okay. Thanks for the link. I thought that once it got to the grub menu it would be something wrong from the linux side. Oh well, more research. 

thanks
scott

---

### Post by boomshop on 2009-02-02
Hi,

I ran in the same problem (but with a partitioned single drive) here and then while fiddling around with macOS/Linux/XP-Config.

Re-syncing the partition tables through rEFIt startup menu always helped me out as I remember.

---

### Post by yepper on 2009-02-02
I wish that wouldve worked, but nonetheless it did not. I had to give up and just drop linux for now. Im thinking its somehow related to the Mac Pro assignments to the drives from the EFI/Refit.... or how I formatted the drives. Because by all accounts, ie. looking at the the grub info, it seems that everything shouldve worked. I wish a Ubuntu Guru would prove me wrong.

Thanks All
-s

---

### Post by cyberdork33 on 2009-02-02
> **boomshop said:**
> Hi,

I ran in the same problem (but with a partitioned single drive) here and then while fiddling around with macOS/Linux/XP-Config.

Re-syncing the partition tables through rEFIt startup menu always helped me out as I remember.
It is a completely different story when you have only one hard drive :)

Really the problem is that whatever hard drive you boot from is seen as the primary hard drive (this is due to how the mac internals work) There are some old posts around that talk about how to work around this here. Basically you have to set the grub configuration to look for things on the primary hard drive, rather than on the drive you'd expect.

---

### Post by pxwpxw on 2009-02-02
> **yepper said:**
> I wish that wouldve worked, but nonetheless it did not. I had to give up and just drop linux for now. Im thinking its somehow related to the Mac Pro assignments to the drives from the EFI/Refit.... or how I formatted the drives. Because by all accounts, ie. looking at the the grub info, it seems that everything shouldve worked. I wish a Ubuntu Guru would prove me wrong.

Thanks All
-s

You could try a grub2 cd,
 
[http://ubuntuforums.org/showthread.php?t=1057600](http://ubuntuforums.org/showthread.php?t=1057600)

 It might help you boot ubuntu. I have not tried it for multiple drives, but it does not depend on anything except finding the linux kernel.

This will list drives and partitions visible.
```

grub> ls -l

```
If it shows all 3 drives then it should boot linux, see the link.

---

