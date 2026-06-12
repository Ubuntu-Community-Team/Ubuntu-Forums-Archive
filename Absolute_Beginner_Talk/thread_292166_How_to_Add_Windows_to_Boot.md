---
title: "How to Add Windows to Boot?"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by domai36 on 2006-11-03
My computer has windows xp and ubuntu but the person who installed linux took Windows off the boot option at the start.  Given the great power of linux it can't do everything windows can (and I don't have the patience or time to figure it all out right now) and I really need to get it back.

I was going to search for this question but I didn't quite know what to search for, so I hope that's excused.

I may also need to supply more info, but any help would be great. Thank you!

---

### Post by Iarwain ben-adar on 2006-11-03
Hi,
could you try to post the output of this command? ```
sudo fdisk -l
```
Note: the -l is a L (but lowercase)

And this command:
```
sudo cat /boot/grub/menu.lst
```


Iarwain

---

### Post by Bachstelze on 2006-11-03
Please paste the output of sudo fdisk -l as well as the contents of /boot/grub/menu.lst

pwn3d:(

---

### Post by domai36 on 2006-11-03
FDisk:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       19457   156288321    7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1340    10763518+   7  HPFS/NTFS
/dev/hdb2            1341        4228    23197860   83  Linux
/dev/hdb3            4229        4865     5116702+  82  Linux swap / Solaris


List:
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
# kopt=root=/dev/hdb2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title           Ubuntu, kernel 2.6.15-27-386
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hdb2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

##title         Ubuntu, kernel 2.6.15-27-386 (recovery mode)
##root          (hd1,1)
##kernel                /boot/vmlinuz-2.6.15-27-386 root=/dev/hdb2 ro single
##initrd                /boot/initrd.img-2.6.15-27-386
##boot

##title         Ubuntu, kernel 2.6.15-26-386
##root          (hd1,1)
##kernel                /boot/vmlinuz-2.6.15-26-386 root=/dev/hdb2 ro quiet spla sh
##initrd                /boot/initrd.img-2.6.15-26-386
##savedefault
##boot

##title         Ubuntu, kernel 2.6.15-26-386 (recovery mode)
##root          (hd1,1)
##kernel                /boot/vmlinuz-2.6.15-26-386 root=/dev/hdb2 ro single
##initrd                /boot/initrd.img-2.6.15-26-386
##boot

##title         Ubuntu, kernel 2.6.15-25-386
##root          (hd1,1)
##kernel                /boot/vmlinuz-2.6.15-25-386 root=/dev/hdb2 ro quiet spla sh
##initrd                /boot/initrd.img-2.6.15-25-386
##savedefault
##boot

##title         Ubuntu, kernel 2.6.15-25-386 (recovery mode)
##root          (hd1,1)
##kernel                /boot/vmlinuz-2.6.15-25-386 root=/dev/hdb2 ro single
##initrd                /boot/initrd.img-2.6.15-25-386
##boot

##title         Ubuntu, kernel 2.6.12-10-386
##root          (hd1,1)
##kernel                /boot/vmlinuz-2.6.12-10-386 root=/dev/hdb2 ro quiet spla sh
##initrd                /boot/initrd.img-2.6.12-10-386
##savedefault
##boot

##title         Ubuntu, kernel 2.6.12-10-386 (recovery mode)
##root          (hd1,1)
##kernel                /boot/vmlinuz-2.6.12-10-386 root=/dev/hdb2 ro single
##initrd                /boot/initrd.img-2.6.12-10-386
##boot

##title         Ubuntu, kernel 2.6.12-9-386
##root          (hd1,1)
##kernel                /boot/vmlinuz-2.6.12-9-386 root=/dev/hdb2 ro quiet splas h
##initrd                /boot/initrd.img-2.6.12-9-386
##savedefault
##boot

##title         Ubuntu, kernel 2.6.12-9-386 (recovery mode)
##root          (hd1,1)
##kernel                /boot/vmlinuz-2.6.12-9-386 root=/dev/hdb2 ro single
##initrd                /boot/initrd.img-2.6.12-9-386
##boot

title           Ubuntu, memtest86+
root            (hd1,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
##title         Microsoft Windows XP Home Edition
##root          (hd1,0)
##savedefault
##makeactive
##map           (hd0) (hd1)
##map           (hd1) (hd0)
##chainloader   +1

---

### Post by Iarwain ben-adar on 2006-11-03
Hi domai36,
It is quite simple :D

Just uncomment the last few lines of your menu.lst.

So it becomes this:
> # menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(,8)
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hdb2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title Ubuntu, kernel 2.6.15-27-386
root (hd1,1)
kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/hdb2 ro quiet splash
initrd /boot/initrd.img-2.6.15-27-386
savedefault
boot

##title Ubuntu, kernel 2.6.15-27-386 (recovery mode)
##root (hd1,1)
##kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/hdb2 ro single
##initrd /boot/initrd.img-2.6.15-27-386
##boot

##title Ubuntu, kernel 2.6.15-26-386
##root (hd1,1)
##kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hdb2 ro quiet spla sh
##initrd /boot/initrd.img-2.6.15-26-386
##savedefault
##boot

##title Ubuntu, kernel 2.6.15-26-386 (recovery mode)
##root (hd1,1)
##kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hdb2 ro single
##initrd /boot/initrd.img-2.6.15-26-386
##boot

##title Ubuntu, kernel 2.6.15-25-386
##root (hd1,1)
##kernel /boot/vmlinuz-2.6.15-25-386 root=/dev/hdb2 ro quiet spla sh
##initrd /boot/initrd.img-2.6.15-25-386
##savedefault
##boot

##title Ubuntu, kernel 2.6.15-25-386 (recovery mode)
##root (hd1,1)
##kernel /boot/vmlinuz-2.6.15-25-386 root=/dev/hdb2 ro single
##initrd /boot/initrd.img-2.6.15-25-386
##boot

##title Ubuntu, kernel 2.6.12-10-386
##root (hd1,1)
##kernel /boot/vmlinuz-2.6.12-10-386 root=/dev/hdb2 ro quiet spla sh
##initrd /boot/initrd.img-2.6.12-10-386
##savedefault
##boot

##title Ubuntu, kernel 2.6.12-10-386 (recovery mode)
##root (hd1,1)
##kernel /boot/vmlinuz-2.6.12-10-386 root=/dev/hdb2 ro single
##initrd /boot/initrd.img-2.6.12-10-386
##boot

##title Ubuntu, kernel 2.6.12-9-386
##root (hd1,1)
##kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hdb2 ro quiet splas h
##initrd /boot/initrd.img-2.6.12-9-386
##savedefault
##boot

##title Ubuntu, kernel 2.6.12-9-386 (recovery mode)
##root (hd1,1)
##kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hdb2 ro single
##initrd /boot/initrd.img-2.6.12-9-386
##boot

title Ubuntu, memtest86+
root (hd1,1)
kernel /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title Microsoft Windows XP Home Edition
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

This should do the trick ;)


Iarwain

---

### Post by domai36 on 2006-11-03
Thank you very much :)

---

### Post by domai36 on 2006-11-03
Shoot... another problem (real newbie here)

It's read-only :<

---

### Post by Iarwain ben-adar on 2006-11-03
Hi,
no problem:
```
sudo nano /boot/grub/menu.lst
```


Iarwain

---

### Post by domai36 on 2006-11-03
It says I need to be the owner... this doesn't sound good.  I thought I was the owner.  It says that the file owner is 'root' as well as the file group. (Both root)

Then below in permissions it says:

Owner: X Read X Write
Group: X Read - Write
Others:X Read - Write

You are not the owner so you can not change permissions.

---

### Post by Iarwain ben-adar on 2006-11-03
Try opening your text editor with root previliges..

```
gksudo gedit
OR
kdesu kate
```
Nautilus is for Ubuntu (Gnome)
and Konquerer for Kubuntu (Kde)


Iarwain

---

### Post by domai36 on 2006-11-03
Yayyy thanks for helping me through my stupid problems :)

---

### Post by Iarwain ben-adar on 2006-11-03
No problem :D

Always happy to make myself useful.


Iarwain

---

