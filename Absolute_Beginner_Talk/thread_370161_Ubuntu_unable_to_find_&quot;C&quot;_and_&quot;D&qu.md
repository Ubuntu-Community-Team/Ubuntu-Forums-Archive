---
title: "Ubuntu unable to find &quot;C&quot; and &quot;D&quot; internal drives"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by sit properly on 2007-02-25
Hi folks, 

I just installed Edgy last night and had a HECK of a time doing it.

Ended up partitioning my "C" (main) drive a couple of times due to hang ups. I think I did the same to my "D" drive too. 

I have four harddrives. And I dual boot. Windows XP recognizes all four, Ubuntu recognizes only two - oddly enough, the two (USB) external drives.

Last night was such a blur, I honestly don't remember when drive I ended up throwing Ubuntu on. I was trying for C drive with windows, but I don't think that worked. I have a hunch it's on one of the externals. 

Anyway, how can I get Ubuntu to recognize the two internals?

Here's my set up:
 
(using fdisk -l in terminal)

[INDENT]Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5665    45504081    7  HPFS/NTFS
/dev/sda2            5666        7742    16683502+   7  HPFS/NTFS
/dev/sda3            7743        9644    15277815   83  Linux
/dev/sda4            9645        9729      682762+   5  Extended
/dev/sda5            9645        9729      682731   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       23489   188675361    7  HPFS/NTFS
/dev/sdb2   *       23490       30117    53239410   83  Linux
/dev/sdb3           30118       30401     2281230    5  Extended
/dev/sdb5           30118       30401     2281198+  82  Linux swap / Solaris

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14593   117218241    7  HPFS/NTFS

Disk /dev/sdf: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       24792   199141708+   7  HPFS/NTFS
[/INDENT]



The drives are partitioned thusly (using cat /boot/grub/device.map):
[INDENT]
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc
(hd3)   /dev/sdd[/INDENT]



And according to cat /boot/grub/menu.lst this is a bunch of other info:

[INDENT]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=42da8259-0a73-4276-8f50-0960602c1f27 ro

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

title           Ubuntu, kernel 2.6.17-11-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=42da8259-0a73-4276-8f50-0960602c1f27 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-386
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=42da8259-0a73-4276-8f50-0960602c1f27 ro single
initrd          /boot/initrd.img-2.6.17-11-386
boot

title           Ubuntu, kernel 2.6.15-28-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-28-386 root=UUID=42da8259-0a73-4276-8f50-0960602c1f27 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-28-386 root=UUID=42da8259-0a73-4276-8f50-0960602c1f27 ro single
initrd          /boot/initrd.img-2.6.15-28-386
boot

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-23-386 root=UUID=42da8259-0a73-4276-8f50-0960602c1f27 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-23-386 root=UUID=42da8259-0a73-4276-8f50-0960602c1f27 ro single
initrd          /boot/initrd.img-2.6.15-23-386
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
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title           Ubuntu, kernel 2.6.15-23-686 (on /dev/sdb2)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.15-23-686 root=/dev/sdb2 ro quiet splash 
initrd          /boot/initrd.img-2.6.15-23-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title           Ubuntu, kernel 2.6.15-23-686 (recovery mode) (on /dev/sdb2)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.15-23-686 root=/dev/sdb2 ro single 
initrd          /boot/initrd.img-2.6.15-23-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title           Ubuntu, memtest86+ (on /dev/sdb2)
root            (hd1,1)
kernel          /boot/memtest86+.bin  
savedefault
boot[/INDENT]




Any help that you can give would be great. I backed up everything on "C" and "D" to the externals, so it's not like I can't access anything, but still, would be nice.

Thanks a bunch!

Eric

---

### Post by Crooksey on 2007-02-25
Looks like you have installed ubuntu on /dev/sda.

Now if you want to see all hardrives, add them to your /etc/fstab.

```

sudo gedit /etc/fstab

```

Then at the bottom add..

```

/dev/sdb1 /mount/location <filesystemtype> defaults 0 1

```

You now need to make that directory exist
```

sudo mkdir /mount/location

```

Thats how to add a partition so ubuntu can see it.

Just copy and paste the line with different mount points and mount locations to other drives.

---

### Post by mahiyar on 2007-02-25
Last night really must have been a blur. I'am not at all an expert, I can just point out observations.  You have installed Linux/Ubuntu twice once on sdb2 and the latest in sda. Does it log in from both locations? sdc and sdf do not have any Linux partitions, so please mount these as suggested above. Since it is NTFS you can read those partitions writing to NTFS is in trial stage and I have not tried it. Here is an example of my entry in fstab
"/**dev/hda1    /media/c ntfs  nls=utf8,umask=0222 0    0**" Instead of /dev/hda1 yours will be /dev/sdc1 etc. Instead of "/media/c" you can make directory under media of any name you like and keep it there.

---

### Post by sit properly on 2007-02-25
I really don't understand any of this. Mount points, locations to other drives... Last night was the first I've ever used a command line. 

Ok, I can get fstab to come up, no problem there. 

I can edit it, sure. But I don't really know what do add.

when you say:
```
/dev/sdb1 /mount/location <filesystemtype> defaults 0 1
```

That's really not exactly what I'm supposed to add, right? I'm supposed to substitute actual places (mount/location). I guess the real problem is that I don't really know what my choices are. And then "filesystemtype".. would that be "NTFS" ? 


And then for making the directory:
```
sudo mkdir /mount/location
```

I'm assuming that "mount" and "location" would be the same in both. But what do I use? I'm afraid that you're going to have to basically spell it all out for me. I'm very much a beginner here. 


And yes, last night was horrible. I do eventually want to get all of the other instances of ubuntu off my drives.

---

