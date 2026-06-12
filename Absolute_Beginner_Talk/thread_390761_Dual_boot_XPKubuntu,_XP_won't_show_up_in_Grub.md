---
title: "Dual boot XP/Kubuntu, XP won't show up in Grub"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by jbsabre on 2007-03-22
Hi all,

I'm new to linux.  After doing some research I decided to dual boot Kubuntu on my XP home computer.  I got Partition Magic and repartitioned my hard drive.  It now has 5 paritions in the following order:
1- NTFS (XP)
2- FAT32 (XP backup)
3- ext3 (for linux)
4- swap
5- FAT32 (for storage)

After partitioning the hard drive I booted windows up again to make sure it worked.  Windows worked fine.  I then restarted my computer and booted up Kubuntu from the live cd.  I then installed Kubuntu, and the installation went great.  Once all the updates were finished, I restarted my computer again to make sure windows was there.  Unfortunately it didn't show up in grub.  Once the grub started initializing I hit <Tab> and Kubuntu was the only thing in the menu.  

After reading many forums I found that it's not an uncommon problem, but I couldn't find anyone with the exact problem so I'm still not sure about the fix.  I could tell you what I think the problem is, but it'd just be a guess so I'll let you tell me.  fdisk -l and /boot/grub/menu.lst will be posted below.  Thanks in advance for your help!

root@jb-desktop:/home/jb# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10837    87048171    7  HPFS/NTFS
/dev/sda2           10838       11986     9229342+   c  W95 FAT32 (LBA)
/dev/sda3           19694       30401    86012010    f  W95 Ext'd (LBA)
/dev/sda4           11987       19693    61906446   83  Linux
/dev/sda5           19694       19954     2096451   82  Linux swap / Solaris
/dev/sda6           19955       30401    83915496    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdf: 32 MB, 32768000 bytes
2 heads, 32 sectors/track, 1000 cylinders
Units = cylinders of 64 * 512 = 32768 bytes

   Device Boot      Start         End      Blocks   Id  System


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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# rootnoverify	(hd0,0)
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
# kopt=root=UUID=e0f4e656-c92f-4757-b3f3-09fb31f70ece ro
# kopt_2_6=root=/dev/sda4 ro

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

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda4 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda4 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda4 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda4 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by anaconda on 2007-03-22
> **jbsabre said:**
> 

# examples
#
# title		Windows 95/98/NT/2000
# rootnoverify	(hd0,0)
# chainloader	+1
#


You just need to edit your grub -configuration file:
open a terminal and type this:
sudo nano /boot/grub/menu.lst

and remove the comments "#" in front of the above lines (in the example above) and save With Ctrl-x.. should work the next time you boot.
and the password the sudo -command will ask is your normal password..

---

### Post by jbsabre on 2007-03-22
Anaconda,

Thank you so much!  I edited the menu.lst and rebooted.  It works great now!

---

