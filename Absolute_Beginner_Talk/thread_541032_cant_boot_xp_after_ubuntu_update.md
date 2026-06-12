---
title: "cant boot xp after ubuntu update"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by panchkapunch on 2007-09-02
Hi 
 After running ubuntu upgrades ,my sda (1)drive has vanished
i cant boot wid win xp now
dual boot was working fine in ma system before installing the updtes
after system reboot,cant boot wid xp
xp partition not visible
ny solutions????????

---

### Post by por100pre1 on 2007-09-02
If you can login into Ubuntu:

```
sudo fdisk -l
```

Post the results.

```
cat /boot/grub/menu.lst
```

Post these results too.

---

### Post by terabyte1 on 2007-09-02
Hmm. I've had this when upgrading. Sometimes your bootloader, "Grub" can lose some details and becomes broken. If this is so you can re-load with the live CD and look for a line which says repair if bootloader is broken. and click on that. It should fix the problem.


Either way someone here can tell you how to fix the bootloader as I think it has a lot to do with that.

I do hope that helps! :)

Terabyte1

---

### Post by panchkapunch on 2007-09-02
@poor100
Results: fdisk-l
asked for password
then showed command not found
result:cat.........
no such file or directory

---

### Post by Arwen on 2007-09-02
menu.lst is your filesystem,in directory named boot,which has a directory named grub where you can find menu.lst.
I'ts **fdisk -l**,space between k and "-"

---

### Post by por100pre1 on 2007-09-02
> **Arwen said:**
> menu.lst is your filesystem,in directory named boot,which has a directory named grub where you can find menu.lst.
I'ts **fdisk -l**,space between k and "-"

fdisk -l has already an space. About menu.lst I got it where I posted, sorry for any inconveniences. :)

---

### Post by por100pre1 on 2007-09-02
> **panchkapunch said:**
> @poor100
Results: fdisk-l
asked for password
then showed command not found
result:cat.........
no such file or directory

Use fdisk -l with an space after k...

---

### Post by panchkapunch on 2007-09-02
@arwen/poor100
Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4871    39126276    7  HPFS/NTFS
/dev/sda2            6451        7297     6796408+  1c  Hidden W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3            4872        4993      979965   82  Linux swap / Solaris
/dev/sda4            4994        6450    11703352+  83  Linux

Partition table entries are not in disk order
THIS POPPED UP AFTER fdisk -l

---

### Post by Duck2006 on 2007-09-02
sudo fdisk -l

---

### Post by por100pre1 on 2007-09-02
> **panchkapunch said:**
> @arwen/poor100
Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4871    39126276    7  HPFS/NTFS
/dev/sda2            6451        7297     6796408+  1c  Hidden W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3            4872        4993      979965   82  Linux swap / Solaris
/dev/sda4            4994        6450    11703352+  83  Linux

Partition table entries are not in disk order
THIS POPPED UP AFTER fdisk -l

Your windows partition seems to be there. Now type:

 ```
cat 
``` (with a space after cat), look for menu.lst file (it should be in the boot folder) and drag and drop it into the terminal window... then type ENTER

---

### Post by por100pre1 on 2007-09-02
Can't you find menu.lst? Let's find it:

```
locate menu.lst
```

post the results... be sure to use lowercase L in menu.**l**st.

---

### Post by panchkapunch on 2007-09-02
sorry i cudnt log on earlier as there was an internet failure at my place
if u r stil there,this is what i find in menu.lst
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
# kopt=root=UUID=cfc51388-2e47-4cdf-82f1-08405c028eae ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cfc51388-2e47-4cdf-82f1-08405c028eae ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cfc51388-2e47-4cdf-82f1-08405c028eae ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
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
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by por100pre1 on 2007-09-02
I'm just a n00b, but I think the FAT32 partition is messed up. Not sure what to do. :(

---

### Post by por100pre1 on 2007-09-02
Check this [thread]("http://ubuntuforums.org/showthread.php?t=538442") please. Post #5. :-k

---

