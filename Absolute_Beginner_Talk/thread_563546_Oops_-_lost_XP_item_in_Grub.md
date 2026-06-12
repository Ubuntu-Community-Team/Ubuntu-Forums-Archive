---
title: "Oops - lost XP item in Grub"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by DavidJE13 on 2007-09-30
I changed the menu.lst file a while ago, putting my XP partition inside the AUTOMAGIC KERNELS LIST section by mistake, and now an update has wiped it.

To add it back I guess I just need to add something similar to;
title		Windows XP
root		(hd0,0)

(this time outside the automagic bit)

but I don't know what the hd0,0 should be, since I can't remember the number of the partition XP is on. How can I find that out? (hd0,0 doesn't work - I tried it already)

---

### Post by cursebg on 2007-09-30
Open gparted (GNOME Partition manager) and check which volume is the ntfs one.

Here's my section for Windows XP :
> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows NT/2000/XP (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1


---

### Post by DavidJE13 on 2007-09-30
It shows the ntfs partition at the top of the list, as /dev/sda1 and first sector at 63 if that helps
But how do I convert that to a hd0,0 type address?

---

### Post by forestpixie on 2007-09-30
the numbers in hd0,0 work this way 
- first number is number of physical drive, second number is number of partition

so hd0,0 would refer to first drive and first partition
    hd1,2 would refer to second drive and third partition

if you do ```
sudo fdisk -l
``` you'll get a list of your drives

---

### Post by DavidJE13 on 2007-09-30
from the output of that, it's looking like it should be 0,0. Which makes me wonder why it doesn't work...

> dave@dave-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15200   122093968+   7  HPFS/NTFS < THIS IS THE PARTITION
/dev/sda2           15201       30023   119065747+  83  Linux < THIS IS THE LINUX PARTITION - listed as hd0,1 in menu.lst
/dev/sda3           30024       30401     3036285   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       24321   195350400    f  W95 Ext'd (LBA)
/dev/sdb5               2       24321   195350368+   7  HPFS/NTFS

---

### Post by DavidJE13 on 2007-09-30
Just in case - here's exactly what my menu.lst file looks like with my attempt at an XP entry;

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

title		Windows XP
root		(hd0,0)
quiet
savedefault

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
# kopt=root=UUID=1df1da80-847a-48a1-9501-80b5a4a56421 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=1df1da80-847a-48a1-9501-80b5a4a56421 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=1df1da80-847a-48a1-9501-80b5a4a56421 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


---

### Post by DavidJE13 on 2007-09-30
Nevermind - I found the fix

I needed to add the chainloader +1 line to the entry.

Thanks for the help :)

---

