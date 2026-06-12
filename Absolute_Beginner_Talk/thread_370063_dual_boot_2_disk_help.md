---
title: "dual boot 2 disk help"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by theenglishmidget on 2007-02-25
i am new to linux for the most part. i just received a new computer with 2 hard drives. i decided to put xp on one and ubuntu on the other. i followed many threads and i installed both without flaws. when i boot up my system i get to the grub loader where it shows ubuntu and xp. i boot into ubuntu fine, but when i try xp it says error 21: selected disc does not exist. when i unplug my linux hd xp boots fine. if have tried editing the menu.list many times with no luck. I would be eternally grateful to whomever could help me solve this problem. 

Thanks in advance, Jack

---

### Post by overdrank on 2007-02-25
> **theenglishmidget said:**
> i am new to linux for the most part. i just received a new computer with 2 hard drives. i decided to put xp on one and ubuntu on the other. i followed many threads and i installed both without flaws. when i boot up my system i get to the grub loader where it shows ubuntu and xp. i boot into ubuntu fine, but when i try xp it says error 21: selected disc does not exist. when i unplug my linux hd xp boots fine. if have tried editing the menu.list many times with no luck. I would be eternally grateful to whomever could help me solve this problem. 

Thanks in advance, Jack

This thread may help. 
[http://ubuntuforums.org/showthread.php?t=369966](http://ubuntuforums.org/showthread.php?t=369966)

---

### Post by confused57 on 2007-02-25
> **theenglishmidget said:**
> i am new to linux for the most part. i just received a new computer with 2 hard drives. i decided to put xp on one and ubuntu on the other. i followed many threads and i installed both without flaws. when i boot up my system i get to the grub loader where it shows ubuntu and xp. i boot into ubuntu fine, but when i try xp it says error 21: selected disc does not exist. when i unplug my linux hd xp boots fine. if have tried editing the menu.list many times with no luck. I would be eternally grateful to whomever could help me solve this problem. 

Thanks in advance, Jack

Are both the drives internal hard drives?  If so, you might want to read this thread:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

and open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
the -l is a small "L"

and

```
cat /boot/grub/menu.lst
```
menu.lst is short for menu.list
you probably just need to post the entries to boot Ubuntu & Windows

---

### Post by theenglishmidget on 2007-02-25
Disk /dev/hda: 10.2 GB, 10204766208 bytes
255 heads, 63 sectors/track, 1240 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1185     9518481   83  Linux
/dev/hda2            1186        1240      441787+   5  Extended
/dev/hda5            1186        1240      441756   82  Linux swap / Solaris

Disk /dev/hdb: 30.0 GB, 30060527616 bytes
255 heads, 63 sectors/track, 3654 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3653    29342691    7  HPFS/NTFS


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
# kopt=root=UUID=afe913e2-3e3e-47fb-9a92-c7227689349d ro
# kopt_2_6=root=/dev/hda1 ro

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

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title Windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


that other post didnt help sorry paul
the one that you gave me confused was the first one that i used to set it up. i followed it exactly and it didnt work

---

### Post by confused57 on 2007-02-25
You could try changing the line:
```
root   (hd1,0)
```

to 

```
rootnoverify  (hd1,0)
```

Also, are your jumper settings correct for the slave drive with Windows & is the slave drive controller "enabled" or set to "auto" in bios?

---

