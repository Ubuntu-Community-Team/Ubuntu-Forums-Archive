---
title: "[SOLVED] Installed XP and used live disc to recover grub now I can't boot to windows"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2008-02-01
I did my best to follow the instructions here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

and that got me to where I can now boot into Linux with no problems but I can't seem to boot into windows. When I select "windows" from the, is it called "grub" menu, I get some kind of error and pressing any key takes me back to where you select the OS you want to boot into.

Is there some magical way to fix things so that I can boot into Windows when I need to?

---

### Post by Desperate on 2008-02-01
Big Oops eh :)
No worries should be simple. When in Ubuntu do you see your windows part? Is it mounted or just there when you check with Gparted? Is it a RAID or ATA RAID ? I guess we need a bit more about it. Do a search as it is one of the most common mishaps when installing and there will be a standard solution.

Good luck

Richard

---

### Post by jan quark on 2008-02-01
I would always recommend to use the super grub disc to restore the grub
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

can you pls tell us what some kind of error you get ?

---

### Post by boriquajake on 2008-02-01
> **jan quark said:**
> I would always recommend to use the super grub disc to restore the grub
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

can you pls tell us what some kind of error you get ?

Jan Quark

I would love to use SuperGrub. In fact, I have tried to use it but I can't get it to do what I want it to do. Obviously it is that I am too dense. If you there is any way you can explain to me what I need to select once I boot into the supergrub live cd I would gladly try to do it.

By the way, the error message I get is:

Error 11: Unrecognized device string

Whatever that means.

---

### Post by boriquajake on 2008-02-01
> **jan quark said:**
> I would always recommend to use the super grub disc to restore the grub
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

can you pls tell us what some kind of error you get ?

Dear Jan Quark,

I just went back and read my first reply to you and I did not like how it appeared. If it seemed like I was being sarcastic or rude I sincerely apologize.  :)

 Once before read a thread on supergrub (I have been fighting this issue for almost a week now) and I was able to get it to restore my ability to boot into linux but I could not figure out how to restore the option to boot into Windows. I have since reinstalled Windows a couple of times and I can now reliably restore the ability to boot into Linux either using supergrub or the Ubuntu live cd.

Just to give a little bit more information, I am able to see the windows portion of the hard drive (I alloted about 15 GB) and I can go into it and see the program files and all the other windows stuff.

Thanks again for taking the time to look answer.

---

### Post by dstew on 2008-02-01
I don't think you need to use the Supergrub disk, you only need to edit the /boot/grub/menu.lst file. We can help you edit this file. First, from your Ubuntu system, on a command line, enter the command```
sudo fdisk -l
```That will list all your partitions. Post the result to this forum. Then, post the result of```
cat /boot/grub/menu.lst
cat /boot/grub/device.map
```With the information from these, we can tell you pretty well how to edit the menu.lst file to get Windows to boot.

---

### Post by boriquajake on 2008-02-01
OK, the results of ```
sudo fdisk -l
```

are:

> Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       12324    98992498+  83  Linux
/dev/hda2           12325       14264    15583050    7  HPFS/NTFS
/dev/hda3           14265       14593     2642692+   5  Extended
/dev/hda5           14265       14593     2642661   82  Linux swap / Solaris

Disk /dev/mmcblk0: 998 MB, 998768640 bytes
20 heads, 51 sectors/track, 1912 cylinders
Units = cylinders of 1020 * 512 = 522240 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1        1913      975295+   6  FAT16


The results of :
```
cat /boot/grub/menu.lst
``` were

> jake@jake-V2000:~$ cat /boot/grub/menu.lst
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
timeout         3

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=24deff58-f29f-45cc-8074-4c559ce6da12 ro

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
# defoptions=quiet splash vga=792

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
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=24deff58-f29f-45cc-8074-4c559ce6da12 ro quiet splash vga=792
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=24deff58-f29f-45cc-8074-4c559ce6da12 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

title           Windows
rootnoverify    (hd0,
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST


and the results of:

```
cat /boot/grub/device.map
```

were:

> (hd0)   /dev/hda


---

### Post by HammerheadNC on 2008-02-01
> **jan quark said:**
> I would always recommend to use the super grub disc to restore the grub
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

can you pls tell us what some kind of error you get ?
 
I cannot tell you how much I am impressed with the Super Grub disk. After days of reinstalling windows trying to fix the bootmgr missing problem after running a dual boot vista/xp system, I found myself having to yet again reinstall XP today.

Imagine my happiness as I lost the grub with the XP reinstall and it was EASILY and QUICKLY restored with Super Grub disk!

THANKS for the info!!!

Going Ubuntu CRAZY

Hammerhead

---

### Post by dstew on 2008-02-02
Bori, all you need to do is edit the /boot/grub/menu.lst file. The root entry for booting windows is incomplete. Change```

rootnoverify (hd0,

```to```

rootnoverify (hd0,1)
```and it should work.

---

### Post by boriquajake on 2008-02-02
> **dstew said:**
> Bori, all you need to do is edit the /boot/grub/menu.lst file. The root entry for booting windows is incomplete. Change```

rootnoverify (hd0,

```to```

rootnoverify (hd0,1)
```and it should work.

Dude, you are a freaking genius and I thank you!!!

---

