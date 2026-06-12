---
title: "remove dual boot"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by Robert Adornato on 2007-12-19
I started with Ubuntu 6 weeks ago and I love it.  I've installed xubuntu on a small partition(sda3), and it became the default OS.  I want to use sda3 for experiments and to later install other distros to learn more about Linux. How do I tell Grub to return to Ubuntu on sda1 as my default, and keep sda1 as the default when I later install other distros over Xubuntu?  My explorations of the the Community Docs left me confused, as my grub's menu.lst appears to list Ubuntu only once.

Thanks,
Rob Adornato

---

### Post by forestpixie on 2007-12-19
ok so you've installed and you want remove what exactly from the dual boot 

give people a bit more information

---

### Post by LinuxIsInnovation on 2007-12-19
Goto root terminal
type " sudo gedit /boot/grub/menu.lst " without quotes
Remove the OS you want to

BE CAREFUL WHILE HANDLING MENU.LST 
IN CASE YOU SCREW IT UP, log in thru Live CD or Recovery option and restore the backup file

---

### Post by forestpixie on 2007-12-19
that's more like it - :)

post your grub and fdisk, you probably only need to edit the default

```
cat /boot/grub/menu.lst
```
```
sudo fdisk -l
```

get it booting right then look at freeing the partition

PS - if you in future wanted to try xubuntu or any of the buntus you can just aptitude install the relevant desktop

---

### Post by Robert Adornato on 2007-12-19
As I see it, # and ## lines are for my benefit.  If this is true, then only the default & a couple of other lines actually impact grub.  as you will see, this is my current menu.lst, but the Ubuntu installation only happens once.  There's no 2nd OS to remove.



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
default		3

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=8da0c964-414e-4108-8146-774bfcbdaaa7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# defoptions=quiet vga=789 splash

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8da0c964-414e-4108-8146-774bfcbdaaa7 ro quiet vga=789 splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8da0c964-414e-4108-8146-774bfcbdaaa7 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Robert Adornato on 2007-12-19
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6478    52034503+  83  Linux
/dev/sda2            9409        9729     2578432+   5  Extended
/dev/sda3   *        6479        9408    23535225   83  Linux
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris
/dev/sda6            9409        9541     1068259+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by forestpixie on 2007-12-19
so can you post your fdisk please - it could be that when you installed xubuntu to a new partition it is the boot partition and has it's own menu.lst

---

### Post by forestpixie on 2007-12-19
thanks that was telepathic :) I am assuming that when you boot at the moment you get the ubuntu/xubunut dual boot choice

but - as I thought, put your livecd in and boot with it - once it's going use gparted from a terminal, I'm sure it's there somewhere

```
gparted
```

hopefully none of the partitions will be mounted so you can work on them, once it's up - go to sda3 and remove the boot flag, go to sda1 and set the boot flag save and close

run fdsik -l again and the flag (* in fdisk) should be on sda1
close the livecd and try to boot - it should start with ubunut on sda1

post back if you have a problem

in future I think that when you get towards the end of the install procedure there is an 'advanced' option - you can change there where grub goes

---

