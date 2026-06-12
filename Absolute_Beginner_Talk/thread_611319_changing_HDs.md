---
title: "changing HDs?"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by joshuapbell on 2007-11-12
Okay, currently I Have ubuntu (slave) and windows xp (master) dual booting, but I don't want xp any more, so I should be able to take my xp hd out, and make my ubuntu disk the master, then repair the mbr? Yes no?

and if so, what would be the best way of doing this?

Thanks

---

### Post by ubnewbie2 on 2007-11-12
Yes, grab a copy of the bootable CD "Super Grub Disk"  It will make life easier.  Basically you will be writing a grub boot record that will start your ubuntu install using the data in /boot/grub

---

### Post by Sef on 2007-11-12
> Okay, currently I Have ubuntu (slave) and windows xp (master) dual booting, but I don't want xp any more, so I should be able to take my xp hd out, and make my ubuntu disk the master, then repair the mbr? Yes no?

and if so, what would be the best way of doing this?

Yes, here's the link to [Super GRUB Boot Disk]("http://supergrub.forjamari.linex.org/").

---

### Post by joshuapbell on 2007-11-12
> **ubnewbie2 said:**
> Yes, grab a copy of the bootable CD "Super Grub Disk"  It will make life easier.  Basically you will be writing a grub boot record that will start your ubuntu install using the data in /boot/grub


And what do I do with this super grub disk?

I mean I will deffently back stuff up, but I don't want to break stuff if I can avoid it.

Thanks

---

### Post by ubnewbie2 on 2007-11-12
boot from it, and follow the help and menus.  Basically, an automatic linux repair should work fine.

---

### Post by meierfra on 2007-11-12
Actually Super Grub won't be able  to do all the work for you. You will also have to edit 
the file "/boot/grub/menu.lst". If you post the output of

sudo fdisk -l

and

cat /boot/grub/menu.lst.

I can tell you exactly what to do.

---

### Post by joshuapbell on 2007-11-12
> **meierfra said:**
> Actually Super Grub won't be able  to do all the work for you. You will also have to edit 
the file "/boot/grub/menu.lst". If you post the output of

sudo fdisk -l

and

cat /boot/grub/menu.lst.

I can tell you exactly what to do.


results of sudo fdisk -l 

```


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x185f185e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3610ae19

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9545    76670181   83  Linux
/dev/sdb2            9546        9729     1477980    5  Extended
/dev/sdb5            9546        9729     1477948+  82  Linux swap / Solaris
joshua@ubuntu:~$ 

```

and the results of the last one is 
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
# kopt=root=UUID=e1cf271f-096e-4779-9af6-38b22d53034d ro

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
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=e1cf271f-096e-4779-9af6-38b22d53034d ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=e1cf271f-096e-4779-9af6-38b22d53034d ro single
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
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by meierfra on 2007-11-12
Here is what you need to do.
Open a terminal. Then 

```
sudo cd /boot/grub
```
(this changes the current directory to /boot/grub
```
sudo cp menu.lst menu.lst.backup
```
This just creates a back up of the file "menu.lst"

```
gksudo gedit menu.lst
```
This opens the file "menu.lst" in a new window.

Change all "(hd1,0)"  to "(hd0,0)" 
(there  will be four, once "#groot (hd1,0)" and three times "root (hd1,0)"

If you still want to access Windows XP, change the windows item to

title           Microsoft Windows XP Professional
root            (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader     +1

Save the file.

Go back to the   terminal and  type:

```
sudo grub
```

This will get you a "grub>" prompt.

Type
```
root (hd1,O)

setup (hd1)

quit

```

This install Grub  to the mbr of your ubuntu disk,


Reboot from the ubuntu disk. (Either remove your windows disk  or set the bios to boot from the ubuntu disk)
You should  get the Grub Menu and boot into  Ubuntu as usual. (If you didn't remove the windows drive and changed the Windows item in menu.lst, you will also be able to boot into windows) 

If you didn't download "super grub" yet and you don't have a different computer to access the internet, I recommend getting super grub now. If something goes wrong, it will let you boot into ubuntu.

.

---

### Post by joshuapbell on 2007-11-12
> **meierfra said:**
> Here is what you need to do.
Open a terminal. Then 

```
sudo cd /boot/grub
```
(this changes the current directory to /boot/grub
```
sudo cp menu.lst menu.lst.backup
```
This just creates a back up of the file "menu.lst"

```
gksudo gedit menu.lst
```
This opens the file "menu.lst" in a new window.

Change all "(hd1,0)"  to "(hd0,0)" 
(there  will be four, once "#groot (hd1,0)" and three times "root (hd1,0)"

If you still want to access Windows XP, change the windows item to

title           Microsoft Windows XP Professional
root            (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader     +1

Save the file.

Go back to the   terminal and  type:

```
sudo grub
```

This will get you a "grub>" prompt.

Type
```
root (hd1,O)

setup (hd1)

quit

```

This install Grub  to the mbr of your ubuntu disk,


Reboot from the ubuntu disk. (Either remove your windows disk  or set the bios to boot from the ubuntu disk)
You should  get the Grub Menu and boot into  Ubuntu as usual. (If you didn't remove the windows drive and changed the Windows item in menu.lst, you will also be able to boot into windows) 

If you didn't download "super grub" yet and you don't have a different computer to access the internet, I recommend getting super grub now. If something goes wrong, it will let you boot into ubuntu.

.

Okay this worked, but my next question is how do I edit the grub menu so that it boots directly into ubuntu?

---

### Post by ubnewbie2 on 2007-11-13
> **joshuapbell said:**
> Okay this worked, but my next question is how do I edit the grub menu so that it boots directly into ubuntu?

There is a timeout value of 10 seconds defined in that file.  I guess you could make that time very short...

---

### Post by meierfra on 2007-11-13
In menu.lst  change

timeout         10

to

timeout      3

(You can  set it even lower, but don't set it to 0, otherwise you won't be able to change  to recovery mode, if you ever need to)

and change


#hiddenmenu

to 

hiddenmenu

(this will hide the grub menu at boot-up, but it  will show up if you  press Esc)

---

