---
title: "Problem with 2nd HD and leftovers:"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by wyoming on 2007-10-27
I installed 7.10 last night (bad choice already) on a partition created on HD#1 with XP on another partition. During the installation I somehow screwed up by asking Ubuntu to use the entire HD#1. OK, I lost what was on it, but that's OK. I also have a HD#2,that I sue for flightsim, which means that I have to have Win. This HD appears nowhere at boot time but is there in Ubuntu ("75 GB Volume"). I had managed to have 2 different installs of Win for the 2 HD, So I have two questions that I'm completely unable to answer by myself:
1- How can I put HD #2 on the boot menu at startup?
2- How can I get rid of this non-functional entry in the boot menu pointing to an XP that cannot be launched (hal.dll missing) and that I don't need anymore anyways since I converted to Ubuntu and lost everything on it?
Thanks.

---

### Post by MaximusTG on 2007-10-27
The entries that you see when you boot are kept in /boot/grub/menu.lst

To edit this file, type in a terminal:

sudo gedit /boot/grub/menu.lst

Do you really have 2 hd's or just 2 partitions?

If you have 2 HD's and there is in fact an XP installation on HD 2, you could probably change this entry in your menu.lst if it is there..

title           Windows NT/2000/XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1

change (hd0,0) to (hd1,0)

but please post an output of 

sudo fdisk -l

and 

cat /boot/grub/menu.lst

So I can give you more explicit instructions
(again in a terminal)

---

### Post by wyoming on 2007-10-27
Yes I have 2 physical HD, a 250 G, where I intende to put Ubuntu and XP for a while AND an 80 G. Here's the logs:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcfc3cfc3

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xab92ab92

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19173   154007091   83  Linux
/dev/sda2           19174       19929     6072570    5  Extended
/dev/sda5           19174       19929     6072538+  82  Linux swap / Solaris



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
# kopt=root=UUID=026b42ff-8e1e-4ff7-9b07-b54f34df7ad0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=026b42ff-8e1e-4ff7-9b07-b54f34df7ad0 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=026b42ff-8e1e-4ff7-9b07-b54f34df7ad0 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition 160 gig
root            (hd0,0)
savedefault
makeactive
chainloader     +1

Thanks!!!

---

### Post by MaximusTG on 2007-10-28
Well, what I can gather from that is that the entry in your boot menu, that goes to the hal.dll error, is in fact the XP you used for flightsims. 
You can see that, because your Ubuntu entries have

root(hd0,0)

and the XP has

root(hd1,0)

which means it is on a separate physical disk.

So you could try to repair that hal.dll error

see here for a step by step guide to possible solutions:

[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)

You need to start with step 3

Good luck!

---

### Post by wyoming on 2007-10-28
Yes, you were right. I can now access my HD#2.Thanks a lot Max! Appreciate the help very much.

---

