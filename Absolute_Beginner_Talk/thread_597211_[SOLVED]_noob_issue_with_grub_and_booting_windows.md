---
title: "[SOLVED] noob: issue with grub and booting windows"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by jedinite7 on 2007-10-30
First time working with Linux and installing Ubuntu 7.10 specifically.  I am trying to dual boot windows XP and Ubuntu.  I apparently did not set up GRUB or my partitions correctly.  When I boot, GRUB shows up and Ubuntu and Windows are listed.  Ubuntu loads perfectly although I cannot get access to my windows partition.  When I select windows from the GRUB list, it loads GRUB again.  I tried changing the information in my menu.lst but no combination worked and resulted in different errors when trying to boot windows.  These are the outputs most people ask for when trying to diagnose the situation so I thought I would include them upfront.  Thanks.  

fdisk -l
```

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x020b020a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           7        1090     8707230    7  HPFS/NTFS
/dev/sda2            1091        1986     7197120   83  Linux
/dev/sda3            1987        2432     3582495    5  Extended
/dev/sda4               1           6       48163+  83  Linux
/dev/sda5            1987        2368     3068383+   b  W95 FAT32
/dev/sda6            2369        2432      514048+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1031 MB, 1031798784 bytes
16 heads, 32 sectors/track, 3936 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3936     1007600    e  W95 FAT16 (LBA)
```


df -l
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2              7083968   2309948   4414164  35% /
varrun                  127928        84    127844   1% /var/run
varlock                 127928         0    127928   0% /var/lock
udev                    127928        80    127848   1% /dev
devshm                  127928         0    127928   0% /dev/shm
lrm                     127928     34696     93232  28% /lib/modules/2.6.22-14-generic/volatile
/dev/sda4                46633     22625     21600  52% /boot
/dev/sda5              3062384         4   3062380   1% /shared
/dev/sdb1              1007328    836640    170688  84% /media/THUMB DRIVE
```


cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=454d2817-d57f-44ad-afa6-1f2b5fe3ac72 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=143f84b3-abb5-4073-87b2-4efb4d689a99 /boot           ext3    defaults        0       2
# /dev/sda5
UUID=4721-382E  /shared         vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=4264B8B564B8ACD3 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=278a6b8f-22b4-4e5b-80a7-a51ac09f7c6f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

mount
```
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda4 on /boot type ext3 (rw)
/dev/sda5 on /shared type vfat (rw,utf8,umask=007,gid=46)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb1 on /media/THUMB DRIVE type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
```

---

### Post by Nano Geek on 2007-10-30
Did you try [reinstalling Grub?]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-7fb1c88570b006aa14b7daaef2238b432b7f73c8")

---

### Post by jedinite7 on 2007-10-30
Just tried it, and it gives me the same result as before.  I hit boot windows and it briefly says Starting stage 2 grub and then I get the menu back again.  It may help to note that I set my partitions up like this.

primary ext3 boot 50 MB
primary ntfs windows ~ 9GB
primary ext3 Linux root ~7 GB
extended ~3GB
   logical fat32 shared 2.5GB
   logical swap 512 MB

I thought I installed grub in the boot partition, but now am not sure. Any help is appreciated.

---

### Post by Nano Geek on 2007-10-30
I'm afraid that my knowledge of Grub ends there. The only thing that I can think of is reinstalling Windows or Ubuntu without a boot partition.
I'm sorry that I wasn't much help.

One last thing, did you have a previous Ubuntu install on your computer before this problem started?

---

### Post by jedinite7 on 2007-10-30
no previous version of ubuntu installed.  I have no problem reinstalling ubuntu if that helps, but I do not see how it really would since it boots and runs fine.  I would prefer not to reinstall windows if at all possible.  Thanks for the help.  

Is it possible that I put GRUB in the windows partition and overwrote some important boot information.  Any more info or resources are appreciated.  Thanks.

---

### Post by rickycodie on 2007-10-30
try posting your grub.conf here.

---

### Post by jedinite7 on 2007-10-30
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
# kopt=root=UUID=454d2817-d57f-44ad-afa6-1f2b5fe3ac72 ro

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
kernel		/vmlinuz-2.6.22-14-generic root=UUID=454d2817-d57f-44ad-afa6-1f2b5fe3ac72 ro quiet splash vga=791
initrd		/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=454d2817-d57f-44ad-afa6-1f2b5fe3ac72 ro single
initrd		/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,3)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1

```

---

### Post by rickycodie on 2007-10-30
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1

it should read 

# title		Windows 95/98/NT/2000
# root		(hd0,1 or 2 or whatever your window partition is on)
# makeactive
# chainloader	+1

,your grub installs to hd0,0 so if this is really where window was it is not there anymore

---

### Post by jedinite7 on 2007-10-30
where is grub.conf

---

### Post by rickycodie on 2007-10-30
sorry it isn't called that. i am in class taking notes while helping you. see previous post for solution.

---

### Post by jedinite7 on 2007-10-30
tried (hd0, 1)  it says grub error 13.  invalid...
and (hd0, 2) says starting.. and then freezes

it looks like I installed grub on my windows partition.  Which probably explains why I cannot mount the windows partition. 

Anyone know of a way to reverse that or at the very least mount the windows so I can get some data off of it.  I backed up the most important information but would be interested in getting some other stuff off of it.  Thanks.

---

### Post by jedinite7 on 2007-10-30
I found this post that describes my problem [http://ubuntuforums.org/archive/index.php/t-54468.html](http://ubuntuforums.org/archive/index.php/t-54468.html)

I ran testdisk replaced the boot sector of my ntfs partition with the backup boot sector.  I am now able to boot to windows with no problems.  Also GRUB and Ubuntu work great.  Thanks for all the help in this forum.

---

### Post by rickycodie on 2007-10-30
any time.

---

