---
title: "ubuntu there xp pro disappeared"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by metzy85 on 2008-03-16
so last night before i want to bed i installed ubuntu and this morning when i woke up and boot me laptop i found that my xp pro is not in the boot menu at all idk where it went i instlla ubuntu 7.10 on a secondary partition which is about 14gb and then i have a 43gb primary one wit my xp pro how do i have xp on the boot order.

---

### Post by sandysandy on 2008-03-16
just make an entry for windows in ur menu.lst file on ubuntu.

have a look at this thread

[http://ubuntuforums.org/showthread.php?t=551558](http://ubuntuforums.org/showthread.php?t=551558)

regards

---

### Post by kbless7 on 2008-03-16
Grub writes over the MBR, so Windows is recognized at first. Type this in the terminal

```
sudo gedit /boot/grub/menu.lst
```

Go down to the end of the file and add

```
title     Windows XP
root     (hd0,1)
makeactive
chainloader +1
```

That should allow you to be able to boot into windows now.

---

### Post by metzy85 on 2008-03-16
it did not said that it was the incorrect command. 

hears wut my grub file looks like idk if this will help 

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
timeout		30

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
# kopt=root=UUID=8e80e7ce-be88-4633-a64c-0000ade44eb3 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8e80e7ce-be88-4633-a64c-0000ade44eb3 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8e80e7ce-be88-4633-a64c-0000ade44eb3 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title     Windows XP
root     (hd0,1)
makeactive
chainloader +1

________________________________________________

i have a single hard drive jsut two partitoins my windows is the rpimary one and my ubuntu is the secondary

---

### Post by alzie on 2008-03-16
> title Windows XP
root (hd0,1)
makeactive
chainloader +1

Change root (hd0,1) to root (hd0,0) and you should be all set.  :)

---

### Post by proalan on 2008-03-16
Your problem is that you defined the root of ubuntu and windows as the same values

root (hd0,1)

if your ubuntu boots properly as it is, then the windows parition is either

root (hd0,0) or root(hd0,2).

---

### Post by metzy85 on 2008-03-16
sadly niether worked hear is my f disk of things

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        5737    46074420    f  W95 Ext'd (LBA)
/dev/sda2   *        5738        7295    12514635   83  Linux
/dev/sda5               2        5737    46074388+   7  HPFS/NTFS
ian@ian-laptop:~$

---

### Post by durand on 2008-03-16
Make that root (hd0,4) for windows

---

### Post by metzy85 on 2008-03-16
sadly still nothing got a error 12 invalid device requested. idk wut the heck is going on wit it

---

### Post by alzie on 2008-03-16
Changing to root (hd0,2) is the next option.  There is only the three options.

---

### Post by metzy85 on 2008-03-16
jsut started over got it working so werid y this would happen do u know a cause. thanks for ur help though

---

