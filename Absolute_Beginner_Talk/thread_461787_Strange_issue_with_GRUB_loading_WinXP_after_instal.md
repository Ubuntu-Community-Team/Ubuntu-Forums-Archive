---
title: "Strange issue with GRUB loading WinXP after installation of Feisty"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by ichiball on 2007-06-02
Hi all,

So here's my predicament...

I have a WinXP install on my computer and previously had Edgy installed as well.  I recently installed Feisty (with Alternate AMD64 installed in text) and now my GRUB loader is acting kinda funky.  Originally I had problems booting Feisty, but then I managed to fix that by editing the menu.lst file with the help of some of the posts in this forum (somehow it was pointing to the wrong partitions on the wrong disks).  Now, however, I get a strange errors when I try to boot WinXP.

**This is what I get:**

Starting up...
Remove disks or other media.*<-- no media is inserted in any of the drives or usb ports -->*
Press any key to restart. *<-- I press 'any' key -->*

The next thing is see is:

NVIDIA Boot Agent 227.0525 *<-- I assume because I have nForce4 chipset, but I'm not sure what it's doing this for -->*
Copyright (c) 2001-2005 NVIDIA Corporation
Copyright (c) 1997-2000 Intel Corporation

*<-- nothing happens for about 30 secs -->*

PXE-E61:  Media Test Failure, Check Cable
PXE-M0F:Exiting NVIDIA Boot Agent

*<-- then the process repeats itself-->*

NVIDIA Boot Agent 227.0525 <-- I assume because I have nForce4 chipset
Copyright (c) 2001-2005 NVIDIA Corporation
Copyright (c) 1997-2000 Intel Corporation

*<-- nothing happens for about 30 secs -->*

PXE-E61:  Media Test Failure, Check Cable
PXE-M0F:Exiting NVIDIA Boot Agent

DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER.

*<-- I press 'Enter' -->*

GRUB loads up again and I select WinXP and this time it finally boots up.


**sudo fdisk -l returns this:**

Disk /dev/sda: 500.1 GB, 500107862016 bytes 
255 heads, 63 sectors/track, 60801 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1       10199    81920128+   7  HPFS/NTFS 
Partition 1 does not end on cylinder boundary. 
/dev/sda2           10199       55913   367200981+   f  W95 Ext'd (LBA) 
/dev/sda3           55914       60801    39262860   83  Linux 
/dev/sda5           10199       22947   102400168+   7  HPFS/NTFS 
/dev/sda6           22947       35696   102400168+   7  HPFS/NTFS 
/dev/sda7           35696       55702   160703392+   7  HPFS/NTFS 
/dev/sda8           55703       55913     1694826   82  Linux swap / Solaris 

Disk /dev/hda: 500.1 GB, 500107862016 bytes 
255 heads, 63 sectors/track, 60801 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 

   Device Boot      Start         End      Blocks   Id  System 
/dev/hda1   *           1        4079    32764536    c  W95 FAT32 (LBA) 
/dev/hda2            4080       60801   455619465    7  HPFS/NTFS 


**sudo gedit /boot/grub/menu.lst returns this:**

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
default		4 

## timeout sec 
# Set a timeout, in SEC seconds, before automatically booting the default entry 
# (normally the first entry defined). 
timeout		15 

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
# kopt=root=UUID=1bb706be-ca2e-4560-be13-8c672b6fe757 ro 

## Setup crashdump menu entries 
## e.g. crashdump=1 
# crashdump=0 

## default grub root device 
## e.g. groot=(hd0,0) 
# groot=(hd1,2) 

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
root		(hd0,2) 
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=1bb706be-ca2e-4560-be13-8c672b6fe757 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic 
quiet 

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) 
root		(hd0,2) 
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=1bb706be-ca2e-4560-be13-8c672b6fe757 ro single 
initrd		/boot/initrd.img-2.6.20-15-generic 

title		Ubuntu, memtest86+ 
root		(hd0,2) 
kernel		/boot/memtest86+.bin 
quiet 

### END DEBIAN AUTOMAGIC KERNELS LIST 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 
root 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda1 
title		Windows XP Media Center Edition 
root		(hd1,0) 
savedefault 
makeactive 
map		(hd0) (hd1) 
map		(hd1) (hd0) 
chainloader	+1 

At this point, I'm totally lost and have no idea how to fix this.  Any help would be greatly appreciated.

Thanks!

---

