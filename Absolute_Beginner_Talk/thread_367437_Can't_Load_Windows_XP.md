---
title: "Can't Load Windows XP"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by Cre-ve on 2007-02-22
I'm very new to Ubuntu. I installed it but I tired to get into windows XP and it won't go in there. I'm having the following problem.

root (hd0,0)
Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

This is what i get when i type in fdisk -l
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13034   104695573+   7  HPFS/NTFS
/dev/sda2           29252       30401     9230760    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3           13035       28591   124961602+  83  Linux
/dev/sda4           28592       29251     5301450    5  Extended
/dev/sda5           28592       29251     5301418+  82  Linux swap / Solaris



this is what i get when i type in cat /boot/grub/menu.lst
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
# kopt=root=/dev/sda3 ro

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

title           Ubuntu, kernel 2.6.15-28-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.15-28-386
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows XP Media Center Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows NT/2000/XP
root            (hd0,1)
savedefault
makeactive
chainloader     +1


please help. I do want to switch to ubuntu completely in the future but I do need to get to my other HD to access files. 

Please talk me though the steps since I dunno how to edit individual directors within the menus. Thank you in advance for your help.

---

### Post by mykalreborn on 2007-02-22
> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows XP Media Center Edition
root (hd0,0)
savedefault
makeactive
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows NT/2000/XP
root (hd0,1)
savedefault
makeactive
chainloader +1

the problem is here. or so i think. what kind of windows did you install? xp media center or the second one, which i can't really tell what it is. nt/2000/xp ?

---

### Post by Tomosaur on 2007-02-22
The sda2 partition will probably be a recovery partition. I have one on my machine, and it shows up like that. Interestingly, I had this exact same problem - caused by resizing the NTFS partition. Unfortunately, I had to completely reinstall Windows. It doesn't play nice with non-Windows operating systems. You may be able to still mount your hard drive, which should give you a good indication of whether your data is lost, or still there. Boot into Ubuntu, open up a terminal, and type:
```

mkdir windows
sudo mount /dev/hda1 ./windows

```
If it mounts successfully, you can change directory:
```

cd windows
ls

```
and see if your files are still there. Hopefully they will all be fine - and you can set about getting grub to boot into the windows partition successfully.

---

### Post by Cre-ve on 2007-02-22
I'm using Windows XP Media Center Edition.


I tried the mount thing and it said the following:
mount: you must specify the filesystem type

does that mean its not there? or something else is wrong?

---

### Post by Cre-ve on 2007-02-22
i tired doing

sudo mount /dev/sda1 ./windows

this apprently worked...then i tried

cd windows

and it said 
bash: cd: windows: permission denied

---

### Post by FenrisAbraxas on 2007-02-22
> **Cre-ve said:**
> i tired doing

sudo mount /dev/sda1 ./windows

this apprently worked...then i tried

cd windows

and it said 
bash: cd: windows: permission denied

Try with ```
sudo -s -H
cd windows
ls

``` 

hope it works

---

### Post by Cre-ve on 2007-02-22
Yes that did work. Wow i'm so glad all my files hasn't been ereased. I did backup my extra important files in my external hardrive just incase but it would have been a real pain in the rear to have to reinstall all my files again.

Is there some way to access my files through windows? I downloaded Super Gurb Disk and burned the iso into a disk. I dunno if I should proceed with this to install my windows. Thank you very much for the help i really appreciate it.

---

### Post by Cre-ve on 2007-02-22
ok i tried messing with the Super Grub Disk and I still couldn't get windows to load up. I uninstalled Grub and now i have to use the Super Grub Disk to get into Ubuntu. 

Do I have to edit Grub and set my hd as sda1?

---

### Post by gn2 on 2007-02-22
Have you tried using GrubEd?
.
[http://www.ubuntuforums.org/showthread.php?t=228104&highlight=GrubEd](http://www.ubuntuforums.org/showthread.php?t=228104&highlight=GrubEd)
.

---

### Post by Tomosaur on 2007-02-22
GrubEd won't fix this problem, it's basically just for tweaking. You will need to read up on how to fix your particular problem I'm afraid. You can use GrubEd to edit the menu.lst file once you've figured out what needs to be done, but GrubEd itself doesn't have a 'fix it!' option :P

---

