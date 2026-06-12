---
title: "Super Grub Disk is SUPER"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-07-21
After struggling for some weeks to reintroduce the option to boot xp into my boot menu, I eventually managed to mess up my whole system and the boot menu disappeared.
After struggling for a couple of days I gave the Super Grub Disk a try and after around 5 minutes Ubuntu is back with me, and grateful I am.
However, I still cant boot into xp and am considering trying Super Grub to help me with this. I notice that it did give me the option of booting into windows but in doing so I would have wiped the Ubuntu option and I wasn't prepared to do that.
Any suggestions gratefully received.

---

### Post by dingletec on 2007-07-21
Fortunately, the solution will be pretty simple and involve editing the /boot/grub/menu.lst file.  Actually, now that I think of it, if you are not getting the grub bootloader on boot, grub may need to be installed again.  I'm going to assume the easier problem right now.

The /boot/grub/menu.lst file contains a list of (devices,partitions) that you can boot from.  When that gets messed up, you have to figure out which device or partition Windows is on so the menu.lst file can be modified to reflect that.

Before someone can help you with that, you must post the output of a few commands from the terminal (Sorry) when you are booted into Ubuntu.

Partitions Ubuntu sees:

cat /proc/partitions

Information on the partitions:

sudo fdisk -l

If you have more than one harddisk, you may need to look at the output of `cat /proc/partitions/` and run fdisk -l on each.

For instance:

sudo fdisk -l /dev/sda
sudo fdisk -l /dev/sdb

or 

sudo fdisk -l /dev/hda
sudo fdisk -l /dev/hdb

The current contents of the /boot/grub/menu.lst file would be helpful as well:

cat /boot/grub/menu.lst

Anyway, that should get things started.

---

### Post by sailor2001 on 2007-07-21
to set your boot priorities, Count down the options as you boot-up starting with zero....Ubuntu generic  is usually listed the first option there fore is zero.....remember the count to where you want the boot to be.   In the terminal type sudo gedit /boot/grub/menu.lst  and you will see a boot option at the bottom of the first paragraph that is probably listed as zero....change that to the number you want to automatically boot into.  Close and save

---

### Post by Benbow on 2007-07-21
In answer to dingletec


benbow@benbow-desktop:~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
benbow@benbow-desktop:~$ cat /proc/partitions
major minor  #blocks  name

   3    64  156290904 hdb
   3    65    3405748 hdb1
   3    66   42299145 hdb2
   3    67          1 hdb3
   3    68      72292 hdb4
   3    69   56645158 hdb5
   3    70   51616813 hdb6
   3    71    2249068 hdb7
benbow@benbow-desktop:~$ 


And for ;cat /boot/grub/menu.lst

benbow@benbow-desktop:~$ cat /boot/grub/menu.lst

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
default         1

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=2efe0512-a956-405f-886b-7c898c8070c3 ro

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-lowlatency
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-16-lowlatency root=UUID=2efe0512-a956-405f-886b-7c898c8070c3 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-lowlatency
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-lowlatency (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-16-lowlatency root=UUID=2efe0512-a956-405f-886b-7c898c8070c3 ro single
initrd          /boot/initrd.img-2.6.20-16-lowlatency

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=2efe0512-a956-405f-886b-7c898c8070c3 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=2efe0512-a956-405f-886b-7c898c8070c3 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=2efe0512-a956-405f-886b-7c898c8070c3 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=2efe0512-a956-405f-886b-7c898c8070c3 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.17-11-generic root=UUID=2efe0512-a956-405f-886b-7c898c8070c3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.17-11-generic root=UUID=2efe0512-a956-405f-886b-7c898c8070c3 ro single
initrd          /boot/initrd.img-2.6.17-11-generic

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=2efe0512-a956-405f-886b-7c898c8070c3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=2efe0512-a956-405f-886b-7c898c8070c3 ro single
initrd          /boot/initrd.img-2.6.17-10-generic

title           Ubuntu, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


This entry automatically added by the Debian installer for a non-linux OS
on /dev/hdb1
title           Windows NT/2000/XP (loader)
root            (hd0,2)
savedefault
makeactive
chainloader     +1


title Windows Vista
root (hd0,1)
makeactive
chainloader +1

By the way, I have xp NOT vista. I don't know where that came from

In answer to Sailor, I am still working on that.

Thanks to both of you

---

### Post by Benbow on 2007-07-21
With the information which I have given in my last post, can anyone advise me how to revive my lost xp section when I boot up. Ubintu is fine but xp does not appear in the initial boot up.

---

### Post by louieb on 2007-07-21
1st go to figure out where XP resides. Then it just a matter of changing the root statement to point GRUB to your XP install.  
>  benbow@benbow-desktop:~$ sudo fdisk -1
fdisk: invalid option -- 1.

Option needs to be a lowercase L Try that and post the output here. 

```
sudo fdisk -l
```

---

### Post by adrian15 on 2007-07-24
> **Benbow said:**
> After struggling for some weeks to reintroduce the option to boot xp into my boot menu, I eventually managed to mess up my whole system and the boot menu disappeared.
After struggling for a couple of days I gave the Super Grub Disk a try and after around 5 minutes Ubuntu is back with me, and grateful I am.
However, I still cant boot into xp and am considering trying Super Grub to help me with this

It's better to edit menu.lst for adding the Windows boot to your grub menu.
> 
. I notice that it did give me the option of booting into windows but in doing so I would have wiped the Ubuntu option and I wasn't prepared to do that.
Any suggestions gratefully received.

It's not as you said.
Windows -> Boot Windows lets you boot windows WITHOUT modifying your hard disk.

Windows -> Fix Boot of Windows does modify your hard disk so that you can boot windows and as you have said you loose the grub boot.

adrian15

---

