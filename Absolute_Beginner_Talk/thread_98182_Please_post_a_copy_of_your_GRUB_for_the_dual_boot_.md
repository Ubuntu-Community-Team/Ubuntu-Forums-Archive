---
title: "Please post a copy of your GRUB for the dual boot Ubuntu/XP single HDD"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by ukiechris on 2005-12-02
My grub is installed in MRB on the Linux partition (0,2). The windows xp is on 0,1.

The system loads Ubuntu without givign me any choices. I kind of have an idea of what I shold do, but I would like to see someone else's GRUB menu.lst file on a working dual boot machine, with one HDD.

Thanks

---

### Post by amohanty on 2005-12-02
I think it would be easier to help if you posted your menu.lst file and we could point out what (if anything) was wrong even though I dont have a single drive configuration.

AM

---

### Post by juicybananahead on 2005-12-02
Well done on installing Linux! :D Please post what happens when you type in the following at the command line:
```
fdisk -l
```

---

### Post by MichaelM on 2005-12-02
[QUOTE=ukiechris]The system loads Ubuntu without givign me any choices.[/QUOTE]
You mean there's no menu at all? If so, try pushing ESC after the BIOS finishes loading.
And check this section of menu.lst:```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```
Make sure hiddenmenu is commented out.

---

### Post by PizzAp on 2005-12-02
I also like the following at the top of my grub.conf
```

timeout         10

```

Most other os are booted like this:
```

title           windows xp
rootnoverify            (hd0,1)
chainloader     +1

```

If i understand partitioning correctly the MBR (Master Boot Record) resides at the very beginning of the harddisk (first sector, 512bytes).

It is hard to give you more help without knowing your disk layout.

---

### Post by ukiechris on 2005-12-04
Here is my grub:
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
default		0

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdc3 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdc3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdc3 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by deNoobius on 2005-12-04
I have a dual-boot setup with Windows.  Here is the block for Windows that works for me in /boot/grub/menu.lst:


title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

This goes after the end of the default options.

---

### Post by ukiechris on 2005-12-04
Here is sudo fdisk -l

```
Disk /dev/hdc: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1           5       40131   de  Dell Utility
/dev/hdc2   *           6         834     6658942+   7  HPFS/NTFS
/dev/hdc3             835        2362    12273660   83  Linux
/dev/hdc4            2363        2432      562275    5  Extended
/dev/hdc5            2363        2432      562243+  82  Linux swap / Solaris

```

---

### Post by aysiu on 2005-12-04
The relevant portion of my /boot/grub/menu.lst looks like this ```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1
``` And the relevant portion of the output of *sudo fdisk -l* looks like this: ```
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1911    15350076    7  HPFS/NTFS
``` Hope that helps.

---

### Post by IdolizingStewie on 2005-12-04
[QUOTE=MichaelM]You mean there's no menu at all? If so, try pushing ESC after the BIOS finishes loading.
And check this section of menu.lst:```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```
Make sure hiddenmenu is commented out.[/QUOTE]

Judging by the menu.lst you posted, ukiechris, this was your problem. You need that third line there commented out.

---

