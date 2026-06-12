---
title: "XP Ubuntu 7.10 Dual-Boot disappearance -MiND Boggling"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by aljosa2008 on 2008-03-07
Hi! First post on the forum , i have been reading a lot since i've installed ubuntu two weeks ago though! I had windows xp pro on the computer before installing ubuntu and had a little complication initially with the partitions. I succeded finally by installing GUTSY on a partition ( i only have 1 hard drive ) but i can't go back to windows xp anymore. At first grub didn't see it then i went and modified sudo gedit /boot/grub/menu.lst to add windows xp but it gave me a lot of error numbers ( 13 , then 12 , then another one ). I have tried reinstalling the xp cd ( i have 2 different copies in mint condition - no scratches ) but after telling me that it is inspecting system configuration it stays on a black screen so i can't even reinstall it or boot from it to windows. I have also tried burning super grub disk to cd and dvd slowly as an iso but it won't boot even though the cd is the first in line to boot at startup.

[SIZE="4"]**MENU.LST**[/SIZE]
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
# kopt=root=UUID=3d0bcaa3-b6f5-4c30-9664-382c93a584a7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title Microsoft Windows XP
root (hd0,5)
makeactive
chainloader +1

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=3d0bcaa3-b6f5-4c30-9664-382c93a584a7 ro quiet splash
initrd		/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=3d0bcaa3-b6f5-4c30-9664-382c93a584a7 ro single
initrd		/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
kernel		/memtest86+.bin
quiet



### END DEBIAN AUTOMAGIC KERNELS LIST



[SIZE="4"]**sudo fdisk -l **[/SIZE]

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b510b50

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2262    18169483+  83  Linux
/dev/hda2            2530        9727    57817935    f  W95 Ext'd (LBA)
/dev/hda3   *        2263        2529     2144677+  82  Linux swap / Solaris
/dev/hda5            2551        9727    57649221    7  HPFS/NTFS
/dev/hda6            2530        2550      168619+  83  Linux

Partition table entries are not in disk order

[SIZE="4"]**/etc/fstab**[/SIZE]

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=3d0bcaa3-b6f5-4c30-9664-382c93a584a7 /               ext3    defaults,erro$
# /dev/hda6
UUID=1028ca21-e944-4e56-89f6-8019ae903423 /boot           ext3    defaults     $
# /dev/hda5
UUID=A204D81A04D7EEF3 /media/hda5     ntfs    defaults,umask=007,gid=46 0      $
# /dev/hda3
UUID=821eaeb1-3e02-47b8-b2ec-df05196c69d9 none            swap    sw           $
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0



These are all the files that people asked for to see if anything is wrong. If anybody can help it would be appreciated! I hope there's some kind of easy solution that makes me look dumb but solve the problem :lolflag:

---

### Post by cocoKnut on 2008-03-07
Try changing your menu.lst file to reflect this:

title Microsoft Windows XP
root (hd0,4)
makeactive
chainloader +1

That entire part should come after the "### END DEBIAN AUTOMAGIC KERNELS LIST" as it might avoid complications later.
That might fix the problem.

To edit the menu.lst file, enter into the terminal:
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by cocoKnut on 2008-03-07
On second thought, your swap partition is marked as active, which is really peculiar.
You can also try this:

title Microsoft Windows XP
root (hd0,4)
chainloader +1

---

