---
title: "Help me fix fstab and grub"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by SmiLey497 on 2007-03-02
k i deleted my windows partion and everything is screwed, so i mounted my drive in live cd session,

 here is the output of fdisk -l 

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       30049   241368561   83  Linux
/dev/sda3           30050       30401     2827440    5  Extended
/dev/sda5           30050       30401     2827408+  82  Linux swap / Solaris


here is what fstab reads 

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=59812a64-8a54-4b1f-b725-e0beb80ab14e /               ext3    defaults,errors=remount-ro 0       1
#  /dev/sda1    /media/windows ntfs  nls=utf8,umask=0222 0    0
# /dev/sda2
UUID=4B6E-6BC0  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=68e4a937-2c56-4d31-985b-92bc78e2e890 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


and here is my grub menu list

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=59812a64-8a54-4b1f-b725-e0beb80ab14e ro
# kopt_2_6=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1


please help

---

### Post by bodhi.zazen on 2007-03-02
Change your entry in menu.lst to :

> title Ubuntu, kernel 2.6.17-11-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro quiet splash
initrd /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

You should be fine on re-boot.

---

### Post by SmiLey497 on 2007-03-02
don't i gotta fix fstab too?

---

### Post by SmiLey497 on 2007-03-02
> **bodhi.zazen said:**
> Change your entry in menu.lst to :



You should be fine on re-boot.

Grub gives me error 22 no such partition when i try boot into ubuntu

---

### Post by gabng on 2007-03-02
bodhi.zazen: Are you sure his root is on sda2?  From his fdisk output and old fstab, it seems his root is on sda3 and he merged his sda1(ntfs) and sda2(fat32) partitions.  Is that right SmiLey497?

---

### Post by bodhi.zazen on 2007-03-02
Nice ...

The problem is your partition numbers changed.

Try :

1. > title Ubuntu, kernel 2.6.17-11-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro quiet splash
initrd /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot


======


2. If that fails, re-install grub:

Boot your ubuntu live (desktop) CD

Open a terminal

Enter : ```
sudo grub
```

At the grub prompt, enter ;```
find /boot/grub/stage2
```

This will return your root in grub speak, probably (hd0,1) Use this in the following commands (at the grub prompt):

```
root (hd0,x)
setup (hd0)
quit
```

Where root (hd0,x) is the root partition returned with the find command

Reboot ...

---

### Post by SmiLey497 on 2007-03-02
i deleted the ntfs and fat partitions and and put it on my ext3 partition which woul dbe sda2 but in fstab it says its sda3, also when i run find /boot/grub/stage i get  (hd0,1)
 so instead of doing (hd0,0) i should do (hd0,1) on th emenu list?

---

### Post by bodhi.zazen on 2007-03-02
> **gabng said:**
> bodhi.zazen: Are you sure his root is on sda2?  From his fdisk output and old fstab, it seems his root is on sda3 and he merged his sda1(ntfs) and sda2(fat32) partitions.  Is that right SmiLey497?

good question ...

His fstab lists the root partition as sda3, but I do not think this matters as much since fstab is mounting root with UUID.

fdisk lists the only potential root partition as sda2. I am guessing he deleted sda1 (his old windows partition) and  re-sized the Ubuntu partition ?? Not sure how that got us from sda3 to sda2 though ...

I think the mistake I made was assuming grub would see the first partition as (hd0,0), but it seems not, thus my next guess is with (hd0,1), again based on fsdisk ...

The problem will be once we restore his HD boot, we will need to edit /boot/grub/menu.lst ...

Oh poo ... 

Perhaps it is best to re-install grub to both the MBR and Ubuntu partition ...

---

### Post by bodhi.zazen on 2007-03-02
> **SmiLey497 said:**
> i deleted the ntfs and fat partitions and and put it on my ext3 partition which woul dbe sda2 but in fstab it says its sda3, also when i run find /boot/grub/stage i get  (hd0,1)
 so instead of doing (hd0,0) i should do (hd0,1) on th emenu list?

Yep ...

But you also need to change these sections (bold) to this :

> ## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=59812a64-8a54-4b1f-b725-e0beb80ab14e ro
# kopt_2_6=root=/dev/**[color=red]sda2[/color]** ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,**[color=red]1**[/color])

And you should likely update fstab as well ...

> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0

# /dev/[color=red]**sda2**[/color]
UUID=59812a64-8a54-4b1f-b725-e0beb80ab14e / ext3 defaults,errors=remount-ro 0 1

# /dev/sda5
UUID=68e4a937-2c56-4d31-985b-92bc78e2e890 none swap sw 0 0

/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

I do not see a fat or ntfs partition so I removed them fro fstab ;)

---

### Post by SmiLey497 on 2007-03-02
> **bodhi.zazen said:**
> Nice ...

The problem is your partition numbers changed.

Try :

1. 


======


2. If that fails, re-install grub:

Boot your ubuntu live (desktop) CD

Open a terminal

Enter : ```
sudo grub
```

At the grub prompt, enter ;```
find /boot/grub/stage2
```

This will return your root in grub speak, probably (hd0,1) Use this in the following commands (at the grub prompt):

```
root (hd0,x)
setup (hd0)
quit
```

Where root (hd0,x) is the root partition returned with the find command

Reboot ...

changing it to (hd0,1) worked like a charm, after 3 days im back in my OS :)

---

### Post by bodhi.zazen on 2007-03-02
Look up for a few additional fixes ....

I was typing as you were booting ...

---

### Post by SmiLey497 on 2007-03-02
> **bodhi.zazen said:**
> Look up for a few additional fixes ....

I was typing as you were booting ...

done, thank you :)

---

