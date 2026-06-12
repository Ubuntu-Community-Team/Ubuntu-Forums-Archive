---
title: "xp lost in grub"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-07-13
Sorry, posted gobbledy gook! I have lost xp in grub and without it I am lost as I need windows to work my canon mp170 successfully. I work on photographs and Turboprint gives me an awful result (ok for b&w text).
Any ideas?

---

### Post by ReaderRat on 2007-07-13
I didn't quite understand the question, but this may help:
[[color=red]GRUB Manual[/color]](http://www.gnu.org/software/grub/manual/grub.html)

---

### Post by LaRoza on 2007-07-13
> **Benbow said:**
> nnnn

Please state your problem and any error messages you are receiving. Also tell when it last worked and any changes between now and then.

You should post more than that.

---

### Post by Benbow on 2007-07-13
Ok. xp is missing from my boot screen although it is still on my hard drive. I therefore can't boot into it.

---

### Post by annda on 2007-07-13
find out where your xp partition is

```
sudo fdisk -l
```

it is the one with HPFS/NTFS filesystem. if it's hda1 or sda1 put this AT THE END of your /boot/grub/menu.lst

> title		Microsoft Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

otherwise modify this part: (hd0,0) to match your partition
hda2 is hd0,1
hdb1 is hd1,0, etc. computers start counting from 0.

if you are unsure, post the output of 
```
cat /boot/grub/menu.lst
```

---

### Post by Benbow on 2007-07-13
Wow, hope you can make sense of this, I can't.
  

 Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         424     3405748+   b  W95 FAT32
/dev/hdb2   *         425        5690    42299145    7  HPFS/NTFS
/dev/hdb3            5691       19448   110511135    5  Extended
/dev/hdb4           19449       19457       72292+   7  HPFS/NTFS
/dev/hdb5            5691       12742    56645158+   7  HPFS/NTFS
/dev/hdb6   *       12743       19168    51616813+  83  Linux
/dev/hdb7           19169       19448     2249068+  82  Linux swap / Solaris
root@benbow-desktop:/home/benbow# cat /boot/grub/menu.lst

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


title Windows XP
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

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
root            (hd0,1)
savedefault
makeactive
chainloader     +1


title Windows Vista
root (hd0,1)
makeactive
chainloader +1

---

