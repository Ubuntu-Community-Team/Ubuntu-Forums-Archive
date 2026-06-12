---
title: "initramfs error"
date: 2011-12-14
forum: Apple Hardware Users
---

### Post by jmr423 on 2011-12-14
Hey so i have a macbook pro 8.2, i bought it about a week about. It is running lion. I would like to install ubuntu 10.04 onto it but i keep running into issues. The main problem is when i try to boot it i get the 

ERROR (initramfs) Unable to find a medium containing a live file system. 

I tried to install it using bootcamp but i came to the same error. I have installed rEFIt and still no luck. 

Extra info.
Current OS- lion
Ubuntu version- 10.04
Laptop model- macbook pro 8.2 release in October 2011 

2.2GHz Quad-core Intel Core i7
4GB 1333MHz DDR3 SDRAM &#8212; 2x2GB
500GB Serial ATA Drive @ 5400 rpm
SuperDrive 8x (DVD±R DL/DVD±RW/CD-RW)

---

### Post by jmr423 on 2011-12-14
Update--- I tried to install ubuntu 11.10 and i get an error saying its unable to mount the cd well im in the installation menu.

---

### Post by jmr423 on 2011-12-18
anyonee? :P

---

### Post by JackPM on 2011-12-20
Here I am with 10.04 LTS on an iBook.
Follow along and try the below commands.

In lvm (lvm>) try vgdisplay, lscan

Gave up waiting for root device.  Common problems:
- Boot args (cat /proc/cmdline)
 -Check rootdelay= (did the system wait long enough?)
 -Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/EXIFM-root does not exist.  Dropping to shell!

BusysBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of commands.

(initramfs) modprobe dm-mod    #no echo
(initramfs) lvm
lvm> vgchange -a y #message about now active directories
lvm> exit
(initramfs) exit  #Now boots to Ubuntu

Ubuntu 10.04 LTS EXIFM tty1

EXIFM login:


exifm@EXIFM:~$ sudo fdisk -l
/dev/hda
        #                    type name                 length   base     ( size )  system
/dev/hda1     Apple_partition_map Apple                    63 @ 1        ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap untitled               2048 @ 2048     (  1.0M)  NewWorld bootblock
/dev/hda3         Apple_UNIX_SVR2 untitled             499712 @ 4096     (244.0M)  Linux native
/dev/hda4               Linux_LVM untitled           77635584 @ 503808   ( 37.0G)  Unknown
/dev/hda5              Apple_Free Extra                  1984 @ 64       (992.0k)  Free space
/dev/hda6              Apple_Free Extra                   768 @ 78139392 (384.0k)  Free space

Block size=512, Number of Blocks=78140160
DeviceType=0x0, DeviceId=0x0

exifm@EXIFM:~$ vi fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/EXIFM-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/hda3 during installation
UUID=8d9fd512-4f65-4872-94ab-560b12f75812 /boot           ext2    defaults        0       2
/dev/mapper/EXIFM-swap_1 none            swap    sw              0       0

---

