---
title: "grub installation and drives mount problem after windows xp installation"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by nokia1100 on 2007-04-17
hi everybody
initially i have both ubuntu and windows
but i just formatted windows partition after that i tried to recover ubuntu in the following way

live cd is loaded into drive and in the terminal 
grub
find grub stage1 
root ...
..
quit

with this kind grub is installed 
after that i tried to mount drives
like 
sudo mkdir /mnt/d
sudo mount /dev/hda8 /mnt/d

it is mounted when live cd is inside drive

but when i restarted system grub only i am getting 
if i tried click on the ubuntu it is saying "drives are not mounted"

i didnt get how to solve this
anybody plz drag me out of this
thanks and regards
nokia

---

### Post by Iceni on 2007-04-17
A nice guide for mounting things here:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by dstew on 2007-04-17
Hi Nokia, I am trying to understand your problem. It seems to me that you have an Ubuntu system installed on your hard drive, and you tried to re-install grub so that it boots your Ubuntu system. When you boot your computer, you get the grub menu, and when you select Ubuntu, it gives you an error message. Is this correct?

What is the exact error message you get?
We would like to see how your disks are set up. Boot the live CD, open a terminal, enter the command **sudo fdisk -l** and post the result to this forum.

---

### Post by nokia1100 on 2007-04-17
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1009     8104761    b  W95 FAT32
/dev/hda2            1010        9729    70043400    f  W95 Ext'd (LBA)
/dev/hda5            1010        3559    20482843+   b  W95 FAT32
/dev/hda6            3560        6109    20482843+   b  W95 FAT32
/dev/hda7            6110        6874     6144831   83  Linux
/dev/hda8            6875        8914    16386268+  83  Linux
/dev/hda9            8915        9602     5526328+  83  Linux
/dev/hda10           9603        9729     1020096   82  Linux swap / Solaris


this is what i got after fdisk -l

yes dstw , what u told is right
nokia

---

### Post by nokia1100 on 2007-04-17
hi dstew
the error i am getting when clik the ubuntu in grub
Error 17 : can't mount selected partition
please cick any key to continue...

thanks and regards 
nokia

---

### Post by dstew on 2007-04-17
OK, now we need to see your grub menu list file, and probably edit it. You have three linux partitions. Do you know which partition contains the linux system you installed? The grub menu file will be on that partition. If you don't know, we will have to search for it.

Once you know which partition has your linux system, you need to mount it on the temporary file system used by the Live CD in order to edit its files. Assume for now that your linux system is on /dev/hda7. To mount it, you can use the directory /tmp as a mount point, like this:

```
mkdir /tmp/ubuntu
sudo mount -t ext3 /dev/hda7 /tmp/ubuntu
```

Now, your linux file system on /dev/hda7 can be found in /tmp/ubuntu. To see the grub menu file, enter:

```
cat /tmp/ubuntu/boot/grub/menu.lst
```

To edit it, you can use the text editor nano:

```
sudo nano /tmp/ubuntu/boot/grub/menu.lst
```

Copy your menu.lst file and post it to this forum.

---

### Post by nokia1100 on 2007-04-18
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
# kopt=root=/dev/hda10 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,9)

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

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,9)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda10 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,9)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda10 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd0,9)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

