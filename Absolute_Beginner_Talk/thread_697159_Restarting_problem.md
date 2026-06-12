---
title: "Restarting problem"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by anderskitson on 2008-02-14
I am having problems each time I restart my ubuntu 64 machine, i get errors about my drive not unmounting properly
Heres my grub menu below, i can get into ubuntu after i type reboot in after the error goes through. but it happens everytime
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
# WARNING: If you are using dmraid do not use 'savedefault' or your
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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=66d830b6-1006-47f0-be9b-d192d425e576 ro quiet 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=66d830b6-1006-47f0-be9b-d192d425e576 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root





# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Microsoft Windows XP Home Edition
root		(hd0,2)
savedefault
makeactive
chainloader	+1


---

### Post by spiderbatdad on 2008-02-14
not sure, but why is the default kernel (hd0,3) instead of (hd0,0)?

---

### Post by anderskitson on 2008-02-14
well I installed ubuntu 32 bit version first, then xp, then the 64 bit

---

### Post by Zack McCool on 2008-02-14
Please post your fstab.  IME, it is fairly likely that a drive (network share, possibly) is not unmounting cleanly on shutdown.  In my case, my mounts to my Windows server do not disconnect on shutdown.  So, I run a script to unmount them before I do a reboot.

---

### Post by dcstar on 2008-02-14
> **anderskitson said:**
> I am having problems each time I restart my ubuntu 64 machine, i get errors about my drive not unmounting properly
Heres my grub menu below, i can get into ubuntu after i type reboot in after the error goes through. but it happens everytime

Grub is irrelevant to these sort of file system errors, they are caused by incorrect shutdowns, not startups.

What is in the /etc/fstab of the 7.10 system?

---

### Post by anderskitson on 2008-02-14
fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=66d830b6-1006-47f0-be9b-d192d425e576 /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=8b2e66e9-e3f9-4cd8-80b0-9a5b1790ba19 /media/sda1     ext2    defaults        0       2
# /dev/sda3
UUID=0AAFCE7C13D2584C /media/sda3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=594275c0-290c-440d-a35a-5525229a14f0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by polmir on 2008-02-15
Type in terminal
```
sudo apt-get install ntfs-3g
```
and correct your fstab
**ntfs** -> rename to -> **ntfs-3g**
restart Ubuntu

---

### Post by anderskitson on 2008-02-15
it wont let me edit it and save, says i dont have permissions

---

### Post by polmir on 2008-02-15
Type in terminal
```
sudo fdisk -l  /dev/sd*
```
-------------
sd*=sda or hda or sdb or hdb or itd.

and post output of it

---

### Post by oedha on 2008-02-15
open fstab by : sudo gedit /etc/fstab

---

### Post by anderskitson on 2008-02-15
I get an error>  fsck died with exit status 8 so i stil have to type reboot after the error to load ubuntu

---

### Post by polmir on 2008-02-15
```
sudo  cat /var/log/fsc/checkfs
sudo cat /var/log/fsck/checkroot
```
post output of it
or try with liveCD  Ubuntu

---

### Post by anderskitson on 2008-02-15
sudo  cat /var/log/fsc/checkfs
came back with no such file or directory

sudo cat /var/log/fsck/checkroot

> Log of fsck -C -a -t ext2 /dev/sdb4 
Thu Feb 14 22:22:19 2008

fsck 1.40.2 (12-Jul-2007)
/dev/sdb4: clean, 122214/10256384 files, 10864663/20480866 blocks

Thu Feb 14 22:22:19 2008


---

### Post by polmir on 2008-02-15
this is My mistake
I am sorry. Please repeat.
```
sudo cat /var/log/fsck/checkfs
```

---

### Post by anderskitson on 2008-02-15
ok heres the log

> Log of fsck -C -R -A -a 
Thu Feb 14 22:22:19 2008

fsck 1.40.2 (12-Jul-2007)
fsck.ext2: Unable to resolve 'UUID=8b2e66e9-e3f9-4cd8-80b0-9a5b1790ba19'
fsck died with exit status 8

Thu Feb 14 22:22:19 2008

---

### Post by polmir on 2008-02-15
Type:
```
 blkid >wynik.txt
```
or
```
 sudo blkid >wynik.txt
```
and post output of it (file wynik.txt)

---

### Post by anderskitson on 2008-02-15
nothing happens on either, where am i supposed to find this file

---

### Post by polmir on 2008-02-15
You post file "wynik.txt". It is in /home/user_name or /root folder

---

### Post by anderskitson on 2008-02-15
/dev/sdb2: TYPE="swap" UUID="594275c0-290c-440d-a35a-5525229a14f0" 
/dev/sdb3: UUID="AAFCE7C13D2584C" TYPE="ntfs" 
/dev/sda1: UUID="3EAC5174AC512823" LABEL="AndersFiles" TYPE="ntfs" 
/dev/sdb4: UUID="66d830b6-1006-47f0-be9b-d192d425e576" TYPE="ext2"

---

### Post by polmir on 2008-02-16
backup old fstab
```
sudo mv /etc/fstab /etc/fstab.old
```
new fstab```
sudo touch /etc/fstab
```

copy this text to your new fstab
[HTML]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>      <options>                   <dump>  <pass>
proc            /proc           proc         defaults                    0       0

/dev/sdb4       /               ext2         defaults,errors=remount-ro  0       1

/dev/sda1       /media/sda1     ntfs         defaults                    0       0
/dev/sdb3       /media/sda3     ntfs         defaults,umask=007,gid=46   0       0

/dev/sdb2       none            swap         sw                          0       0
/dev/scd0       /media/cdrom0   udf,iso9660  user,noauto,exec            0       0
/dev/fd0        /media/floppy0  auto         rw,user,noauto,exec         0       0
[/HTML]

---

### Post by anderskitson on 2008-02-16
Everything seems fine now, except i get an error for my external hardrive via usb, it works, but i get an error fir it shutting down and booting up

---

