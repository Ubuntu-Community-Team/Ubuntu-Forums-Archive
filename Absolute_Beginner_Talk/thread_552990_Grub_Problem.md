---
title: "Grub Problem"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by bjstabio on 2007-09-17
hda has Kubuntu installed.
hdb has Ubuntu Edgy & Gutsy installed.
My problem is that the os on hda does not show up on the Grub menu, only those on hdb.  Help please.

---

### Post by mikewhatever on 2007-09-17
Post the output of the following commands from the terminal
> cat /boot/grub/menu.lst
sudo fdisk -l

---

### Post by bjstabio on 2007-09-18
Thanks for the response.  Hope this is what you were looking for.

bjstabio@BobbyBuilt-03:~$ cat /boot/grub/menu.lst
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
default         0

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
# kopt=root=UUID=abbe11e9-377d-4e88-b3a0-f9f25a9c77db ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title           Ubuntu gutsy (development branch), kernel 2.6.22-11-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-11-generic root=UUID=abbe11e9-377d-4e88-b3a0-f9f25a9c77db ro quiet splash
initrd          /boot/initrd.img-2.6.22-11-generic
quiet

title           Ubuntu gutsy (development branch), kernel 2.6.22-11-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-11-generic root=UUID=abbe11e9-377d-4e88-b3a0-f9f25a9c77db ro single
initrd          /boot/initrd.img-2.6.22-11-generic

title           Ubuntu gutsy (development branch), kernel 2.6.22-10-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-10-generic root=UUID=abbe11e9-377d-4e88-b3a0-f9f25a9c77db ro quiet splash
initrd          /boot/initrd.img-2.6.22-10-generic
quiet

title           Ubuntu gutsy (development branch), kernel 2.6.22-10-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-10-generic root=UUID=abbe11e9-377d-4e88-b3a0-f9f25a9c77db ro single
initrd          /boot/initrd.img-2.6.22-10-generic

title           Ubuntu gutsy (development branch), memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title           Ubuntu, kernel 2.6.17-12-generic (on /dev/hda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-12-generic root=/dev/hda1 ro quiet splash 
initrd          /boot/initrd.img-2.6.17-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title           Ubuntu, kernel 2.6.17-12-generic (recovery mode) (on /dev/hda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-12-generic root=/dev/hda1 ro single 
initrd          /boot/initrd.img-2.6.17-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title           Ubuntu, kernel 2.6.17-10-generic (on /dev/hda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash 
initrd          /boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title           Ubuntu, kernel 2.6.17-10-generic (recovery mode) (on /dev/hda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single 
initrd          /boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title           Ubuntu, memtest86+ (on /dev/hda1)
root            (hd0,0)
kernel          /boot/memtest86+.bin  
savedefault
boot

bjstabio@BobbyBuilt-03:~$ sudo fdisk -l
[sudo] password for bjstabio:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00030ab3

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       18700   150207718+  83  Linux
/dev/hda2           18701       19457     6080602+   5  Extended
/dev/hda5           18701       19457     6080571   82  Linux swap / Solaris

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000baeea

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9575    76911156   83  Linux
/dev/hdb2           18323       19457     9116887+   5  Extended
/dev/hdb3   *        9576       18322    70260277+  83  Linux
/dev/hdb5           18701       19457     6080571   82  Linux swap / Solaris
/dev/hdb6           18323       18700     3036222   82  Linux swap / Solaris

Partition table entries are not in disk order
bjstabio@BobbyBuilt-03:~$

---

### Post by Bothered on 2007-09-18
The version of grub executed on boot may not be the one whose menu.lst you just posted. Could you type "cat /boot/grub/menu.lst" and post the result from each of your ubuntu installs?

---

### Post by bjstabio on 2007-09-18
How do I do that?

---

### Post by confused57 on 2007-09-18
You can try using a configfile entry to boot Kubuntu:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

Open a terminal:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

Add this entry to the bottom of your menu.lst:
```
title   Kubuntu
configfile (hd1,0)/boot/grub/menu.lst
```

quit & save

---

