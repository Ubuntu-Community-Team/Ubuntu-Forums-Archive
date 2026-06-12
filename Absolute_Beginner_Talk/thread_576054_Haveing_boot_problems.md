---
title: "Haveing boot problems"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by aas452 on 2007-10-14
I have been having trouble booting my machine.

I had a machine with windows on it and wanted to whip the whole drive and just run Ubuntu from this specific machine. The machine I have has 3 SCSI drives and what I did was whip them all and left them unformatted. Then downloaded Ubuntu from the CD, everything went well until it told me to restart the machine and at restart the screen freezes and this message appears

Boot from ATAPI CD-ROM :
Boot from ATAPI CD-ROM :
GRUB

I also then tried to get in to the system from the Live CD and then choose the boot from first disk option and that finally booted the system

I have posted about this issue once before but going to try to be more specific this time - Anyone know whats going on with this???

---

### Post by LowSky on 2007-10-14
What are the machines specs?

Did you check to make sure you have a good Live CD?

---

### Post by aas452 on 2007-10-15
Machine specs-

3 SCSI drives one 18gb and 2 other 34gb.

2gb of ram

2 X 2.4 Xeons

I checked the CD and it checks out fine.

Also checked the grub file in boot.
In the menu.lst file it seem the root section of the file reads a UUID number rather then something like /dev/sda1 /ext3 


Don't know if that makes any sense but I think the system might not know either where grub is or  grub is just shrewrd up in general.

Also I have formated the other two 30gb SCSI drive could this be an issue also???

Any thoughts on a fix???

---

### Post by ghost_ryder35 on 2007-10-15
ubuntu uses UUID numbers instead of /dev/sda/ext3.  I think you need to reinstall and choose the primary hard drive to install too.  If Ubuntu got installed on a slave drive then grub wont load.

---

### Post by aas452 on 2007-10-15
When I do an fdisk -l command it shows up that ubuntu is on the first drive and an * is displayed on the boot column. Should I install Ubuntu on another SCSI drive and see if that works. 

If it helps I could display the code generated from the  fdisk -l command later on 2night (im not on that machine as of right now) as well as the menu.lst file in grub

let me know if anyone else has any ideas on what could be happening

---

### Post by aas452 on 2007-10-27
hi all been still having the problem and just got back to fixing it here is the code I promised

Here is fstab

```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=7003b725-f8bd-444d-b9f6-5ddd9d2a14b1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=72d8ac20-cb95-4282-83b8-24eba215f45b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


```


Here is /boot/grub/menu.lst

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
# kopt=root=UUID=7003b725-f8bd-444d-b9f6-5ddd9d2a14b1 ro

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=7003b725-f8bd-444d-b9f6-5ddd9d2a14b1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=7003b725-f8bd-444d-b9f6-5ddd9d2a14b1 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1



``` 


Here is fdisk -l

```
   

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1155     9277506    7  HPFS/NTFS
/dev/sda2   *        1156        2160     8072662+  83  Linux
/dev/sda3            2161        2212      417690    5  Extended
/dev/sda5            2161        2212      417658+  82  Linux swap / Solaris

Disk /dev/sdb: 36.4 GB, 36401479680 bytes
255 heads, 63 sectors/track, 4425 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4425    35543781    4  FAT16 <32M

Disk /dev/sdc: 36.4 GB, 36401479680 bytes
255 heads, 63 sectors/track, 4425 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4425    35543781    4  FAT16 <32M


```


Please any help would be awesome, I really dont want to go back or depend on windows anymore

Thanks again

---

### Post by aas452 on 2007-11-09
hey was just wondering if anyone knows what is going on with my system, Ive been trying for quit some time now to figure this out , and have been loading ubuntu from the live CD just to get my system running, please I need some help.

---

