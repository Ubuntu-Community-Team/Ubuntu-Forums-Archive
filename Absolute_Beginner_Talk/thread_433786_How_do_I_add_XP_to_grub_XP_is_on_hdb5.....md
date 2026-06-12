---
title: "How do I add XP to grub? XP is on hdb5...."
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by elijahclarity on 2007-05-05
I installed Ubuntu to hdb2 (primary) and XP was on hdb5 (logical).

Ubuntu didnt recognise XP installation.

How do I manually add the XP entry to grub? Plz help.

I tried the following but it doesn't work. Tells me "Invalid device request"

title Windows XP
root (hd1,6)
makeactive
map (hd0,0) (hd1,6)
map (hd1,6) (hd0,0)
rootnoverify (hd1,6)
chainloader +1

Thanks....

---

### Post by Najand on 2007-05-05
Use this one:
```

title Windows XP
root (hd1,6)
makeactive
[COLOR="Red"]map (hd0) (hd1)
map (hd1) (hd0)[/COLOR]
rootnoverify (hd1,6)
chainloader +1

```

---

### Post by elijahclarity on 2007-05-05
I tried that Najand but it doesn't work...tells me the same thing

Error 12: Invalid device request

Press any key to continue....


When I press a key, I get back to the grub menu.  What do I do??

---

### Post by Najand on 2007-05-05
Oh, your windows is on /dev/hdb5. It means it should be:
```

[COLOR="Blue"]root (hd1,4)[/COLOR]

```
Not [COLOR="Red"]root (hd1,6)[/COLOR]!

---

### Post by elijahclarity on 2007-05-05
Sorry that didn't help either. I get the same error.

Anyways this is the output of fdisk -l:

fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+   c  W95 FAT32 (LBA)
/dev/sda2            2433        4864    19535040    f  W95 Ext'd (LBA)
/dev/sda5            2433        4864    19535008+   e  W95 FAT16 (LBA)

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3647    29294496    7  HPFS/NTFS
/dev/sdb2            3648        7294    29294527+  83  Linux
/dev/sdb3   *        7295       12157    39062047+  83  Linux
/dev/sdb4           12158       30515   147460635    5  Extended
/dev/sdb5           12158       25530   107418591    b  W95 FAT32
/dev/sdb6           25531       30393    39062016   83  Linux
/dev/sdb7           30394       30515      979933+  82  Linux swap / Solaris

Hope this info will be useful.

Plz help. I need to go into XP for an important task.

Thanks...

---

### Post by confused57 on 2007-05-05
Post the ouput of:
```
cat /boot/grub/menu.lst
```

---

### Post by elijahclarity on 2007-05-06
cat /boot/grub/menu.lst

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
# kopt=root=UUID=be9c9a5e-0c26-40ab-8030-488c8f52d13d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title           Ubuntu 7.04
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=be9c9a5e-0c26-40ab-8030-488c8f52d13d ro quiet 
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Windows XP
root (hd1,6)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,6)
chainloader +1

title           Ubuntu 7.04 (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=be9c9a5e-0c26-40ab-8030-488c8f52d13d ro single
initrd          /boot/initrd.img-2.6.20-15-generic

#title          Ubuntu, memtest86+
#root           (hd1,1)
#kernel         /boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by confused57 on 2007-05-06
You may have trouble booting Windows on a logical partition, using grub, see reply #3 in this thread:
[http://ubuntuforums.org/showthread.php?t=426919](http://ubuntuforums.org/showthread.php?t=426919)

You could try some different combinations of Window's entries:
```
title Windows XP
rootnoverify  (hd1,4)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

or

```
title Windows XP
rootnoverify  (hd1,4)
makeactive
chainloader +1
```

You might try downloading & burning a Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it might possibly be able to boot your Window's partition or it may be able to reinstall Window's IPL code to the mbr that would allow you to boot Windows(you wouldn't be able to boot Ubuntu, though).

If for some reason you need to reinstall grub to the mbr, you can use the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

What is the NTFS partition on /dev/sdb1?  Your Window's XP is on a FAT partition on /dev/sdb5?

---

### Post by elijahclarity on 2007-05-06
Thanks.....that info helped. I think I'll have to use a 3rd party boot manager, or install XP on primary partition. Can u recommend a good boot manager??

sdbi is just an empty NTFS partitions I think. No need to pay any heed to it. :)
XP is on hdb5 and its a FAT partition.

I already have the Super grub disk and I think I may be able to boot XP with it but I wanna boot Ubuntu too. Do I have to lose one to get one???

I reinstalled grub once (long time back) and lost access to XP. I tried everything but couldn't boot XP. My brother had to reinstall XP. I don't wanna do this again its very unreliable to re-install grub.

---

