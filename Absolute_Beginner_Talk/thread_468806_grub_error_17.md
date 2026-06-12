---
title: "grub error 17"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by doyler78 on 2007-06-09
Had grub error 17. Trying to reinstall grub didn't work and I needed help so had no choice but to fixmbr for winxp so that I could post for help. Now I have windows xp running but cannot access Ubuntu. I had a lot of stuff donwloaded on Ubuntu which I would like access to or I would have a just simply reinstalled as this is only recent installation.
 
Any ways I have booted into Ubuntu with a live cd and here are the contents of:
 
fdisk -l
/boot/grub/device.map
/etc/fstab
 
/boot/grub/menu.lst doesn't exist (guessing that may be part of my probs) so can't post it.
 
fdisk -l contents:
 
```
[SIZE=2]
Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Device Boot Start End Blocks Id System
/dev/hda1 * 1 3952 31744408+ 7 HPFS/NTFS
/dev/hda2 3953 8535 36812947+ 83 Linux
/dev/hda3 8536 24792 130584352+ f W95 Ext'd (LBA)
/dev/hda5 8536 8912 3028189+ 82 Linux swap / Solaris
/dev/hda6 8913 11951 24410736 83 Linux
/dev/hda7 11952 14024 16651341 83 Linux
/dev/hda8 14025 19124 40965718+ 7 HPFS/NTFS
/dev/hda9 19125 24792 45528178+ 83 Linux
Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Device Boot Start End Blocks Id System
/dev/hdb1 * 1 13 104391 83 Linux
/dev/hdb2 14 4865 38973690 7 HPFS/NTFS
[/SIZE]
```
 
device.map contents:
 
```
[SIZE=2]
(fd0) /dev/fd0
(hd0) /dev/hda
(hd1) /dev/hdb
[/SIZE]
```
 
and finally fstab contents:
 
```
[SIZE=2]
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/hda5 swap swap defaults 0 0
[/SIZE]
```
 
I know that:
 
/dev/hda1/ is my windows xp install drive - ntfs
/dev/hda2/ is my ubuntu root - ext3
/dev/hda5/ is my linux swap
/dev/hda6/ is my /home partition - ext3
/dev/hda7 is my /www partition - ext3
/dev/hda8 is a data storage partition in ntfs format
/dev/hda9 is formatted in ext3 (was previously ntfs - created freespace and then formatted the partition in ext3). I needed more space for my home partition as it is nearly out of space. I started using ubuntu much more than I had planned and therefore ran out of space way too quickly.
 
Booting into ubuntu through a livecd and opening and terminal and running sudo grub-install /dev/hda1 just doesn't work.
 
What to do next?
 
Thanks in advance.

---

### Post by confused57 on 2007-06-09
You need to mount your root partition, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

---

### Post by doyler78 on 2007-06-09
Thanks confused57. Let's go again then.
 
fdisk -l
 
```
[SIZE=2]
Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Device Boot Start End Blocks Id System
/dev/hda1 * 1 3952 31744408+ 7 HPFS/NTFS
/dev/hda2 3953 8535 36812947+ 83 Linux
/dev/hda3 8536 24792 130584352+ f W95 Ext'd (LBA)
/dev/hda5 8536 8912 3028189+ 82 Linux swap / Solaris
/dev/hda6 8913 11951 24410736 83 Linux
/dev/hda7 11952 14024 16651341 83 Linux
/dev/hda8 14025 19124 40965718+ 7 HPFS/NTFS
/dev/hda9 19125 24792 45528178+ 83 Linux
Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Device Boot Start End Blocks Id System
/dev/hdb1 * 1 13 104391 83 Linux
/dev/hdb2 14 4865 38973690 7 HPFS/NTFS
Disk /dev/sda: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Device Boot Start End Blocks Id System
/dev/sda1 * 1 7872 2015216 e W95 FAT16 (LBA)
[/SIZE]
```
 
/boot/grub/menu.lst contents:
 
```
[SIZE=2]
# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
# Pretty colours
#color cyan/blue white/blue
## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret
#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=09ee06ca-9599-4a4a-a802-6c9eb4e51716 ro
## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)
## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true
## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false
## Xen hypervisor options to use with the default Xen boot option
# xenhopt=
## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0
## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all
## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true
## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false
## ## End Default Options ##
title Ubuntu, kernel 2.6.20-16-server
root (hd0,2)
kernel /boot/vmlinuz-2.6.20-16-server root=UUID=09ee06ca-9599-4a4a-a802-6c9eb4e51716 ro quiet splash
initrd /boot/initrd.img-2.6.20-16-server
quiet
savedefault
title Ubuntu, kernel 2.6.20-16-server (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.20-16-server root=UUID=09ee06ca-9599-4a4a-a802-6c9eb4e51716 ro single
initrd /boot/initrd.img-2.6.20-16-server
title Ubuntu, kernel 2.6.20-15-server
root (hd0,2)
kernel /boot/vmlinuz-2.6.20-15-server root=UUID=09ee06ca-9599-4a4a-a802-6c9eb4e51716 ro quiet splash
initrd /boot/initrd.img-2.6.20-15-server
quiet
savedefault
title Ubuntu, kernel 2.6.20-15-server (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.20-15-server root=UUID=09ee06ca-9599-4a4a-a802-6c9eb4e51716 ro single
initrd /boot/initrd.img-2.6.20-15-server
title Ubuntu, memtest86+
root (hd0,2)
kernel /boot/memtest86+.bin
quiet
### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root
 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1
[/SIZE]
```
 
/boot/grub/device.map contents:
 
```
[SIZE=2]
(hd0) /dev/hda
(hd1) /dev/hdb
[/SIZE]
```
 
/etc/fstab contents:
 
```
[SIZE=2]
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/hda5 swap swap defaults 0 0
[/SIZE]
```

---

### Post by confused57 on 2007-06-09
The /etc/fstab you posted is the live cd's file, to access your installation's fstab, for example if you "mkdir /media/ubunt", then mounted, it would be:
```
gedit /media/ubuntu/etc/fstab
```

From the output of "sudo fdisk -l", it looks like your root should be (hd0,1).

What you might want to do is download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it should be able to boot your Ubuntu

You probably already know, but you can reinstall grub with the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by doyler78 on 2007-06-09
Thanks a lot. The live cd method worked. I thought I had tried as I had seen that post but must not have. Anyway thanks for that. My next task is how to increase or move my home partition as I have nearly ran out of space and have freed another 43gb however they are not next to eachother on the disk ie hda6 and hda9. Will post that in a new thread if I can't find the answer with a quick a search.

Thanks again.

---

