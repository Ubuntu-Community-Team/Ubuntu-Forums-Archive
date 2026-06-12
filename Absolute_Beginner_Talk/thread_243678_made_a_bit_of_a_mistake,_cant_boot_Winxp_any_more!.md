---
title: "made a bit of a mistake, cant boot Winxp any more!"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by bplus on 2006-08-25
Hi,
I used to have breezy badger and winxp on a dual boot.
I tried to completely wipe my badger install then install  dapper cleanly.
I managed to install dapper but I think i messed up by accidently putting dapper a very small partition. Breezy is gone and I m running dapper. However winxp doesnt appear in the grub boot menu anymore! But all my winxp files are still on their partition. Dapper mounted four drives onto the destop: 

1.my orginal C: drive with winxp on it
2.another windows partition. 
3.hda4 which just has a lost and found folder in it now
4.PQSERVICE which has has fies and folders like: autoexe.bat (this makes me think it ust be something to do with my windows booting process or whatever its called.)

Is there a way to boot windows again?

I ve obviously done something very stupid and would be most grateful if any one could help me out!

thanks.

---

### Post by nrwilk on 2006-08-25
You can reinstall GRUB by inserting your ubuntu install disk and skipping to the GRUB step.  It should detect all your bootable partitions and automatically add entries for them in your menu.lst.

---

### Post by Iarwain ben-adar on 2006-08-25
Hi,
just post the contents of your /etc/fstab and your /boot/grub/menu.lst and the output of this command
```
sudo fdisk -l 
```


Iarwain

---

### Post by bplus on 2006-08-25
fdisk
> 
Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, [/63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         319     2562336   12  Compaq diagnostics
/dev/hda2             320        6230    47480107+   c  W95 FAT32 (LBA)
/dev/hda3            6231        8925    21647587+   f  W95 Ext'd (LBA)
/dev/hda4            8926       12161    25993170   83  Linux
/dev/hda5            6231        8495    18193581    b  W95 FAT32
/dev/hda6            8784        8925     1140583+  82  Linux swap / Solaris
/dev/hda7   *        8496        8766     2176776   83  Linux
/dev/hda8            8767        8783      136521   82  Linux swap / Solaris


contents of fstab
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda2       /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda4       /media/hda4     ext3    defaults        0       2
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0



> 
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
# kopt=root=/dev/hda7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda7 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda7 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


thank you for helping me!

---

### Post by bplus on 2006-08-25
Hi,
I ve just re formatedd everything instead and started afresh so consider this solved!

---

