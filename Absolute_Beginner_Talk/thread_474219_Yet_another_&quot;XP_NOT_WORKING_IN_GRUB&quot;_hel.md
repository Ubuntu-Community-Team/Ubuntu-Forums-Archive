---
title: "Yet another &quot;XP NOT WORKING IN GRUB&quot; help thread"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by hoges on 2007-06-14
Hi there,

My laptop was running dual boot vista/xp, and I think the bootloader was on the vista drive. When I installed ubuntu over vista, grub didn't automatically detect xp.

I know the partition still exists, because it has mounted within gnome as "sda5".

device.map gives:
(hd0)	/dev/sda

shouldn't there be another entry for the xp partition? can i just make one if needed?

this is what I added to menu.lst:
title		Windows XP Professional
map		(hd0)(hd1)
map		(hd1)(hd0)
root		(hd1,0)
savedefault
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST <-- added before this

All the xp data is there and ok, just need it for some uni software. Not a big deal at the moment, as I'm not a uni for a month or so, but I'd like to get it working.

So, if someone could let me know what I need to edit/hack/info to supply to help, please let me know.

Cheers,
Hoges

EDIT: sda5 isn't working under menu.lst either

---

### Post by alienexplorers on 2007-06-14
My entry for XP is listed in menu.lst as:
> title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

This setup runs perfectly on dual boot system.  I beleive Windows must be on the first hard drive to boot correctly.  At least with my windows XP system this is true.

---

### Post by confused57 on 2007-06-14
You need to post the output of:
```
sudo fdisk -l
```
the -l is a lowercase "L"

This will show your partitions, and someone should  be able to suggest an entry to boot Windows.

---

### Post by Inxsible on 2007-06-14
> **hoges said:**
> Hi there,

My laptop was running dual boot vista/xp, and I think the bootloader was on the vista drive. When I installed ubuntu over vista, grub didn't automatically detect xp.

I know the partition still exists, because it has mounted within gnome as "sda5".

device.map gives:
(hd0)	/dev/sda

shouldn't there be another entry for the xp partition? can i just make one if needed?

this is what I added to menu.lst:
title		Windows XP Professional
map		(hd0)(hd1)
map		(hd1)(hd0)
root		(hd1,0)
savedefault
makeactive
chainloader	+1

[COLOR="Red"]### END DEBIAN AUTOMAGIC KERNELS LIST <-- added before this[/COLOR]

All the xp data is there and ok, just need it for some uni software. Not a big deal at the moment, as I'm not a uni for a month or so, but I'd like to get it working.

So, if someone could let me know what I need to edit/hack/info to supply to help, please let me know.

Cheers,
Hoges

EDIT: sda5 isn't working under menu.lst either

you definitely DO NOT want to add Windows entry before the End Debian.....line
The next update of the Ubuntu kernel will erase your Windows entry. Post back your /boot/grub/menu.lst in its entirety. 

Also post the output of ```
sudo fdisk -l
``` -l is lowercase L

---

### Post by hoges on 2007-06-15
Alright, I'd forgotten how quick the responses in this forum were. Thanks for the pointers...

Here's the output of fdisk -l:

```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             193        2623    19527007+   b  W95 FAT32
/dev/sda3            2624       12160    76605952+   f  W95 Ext'd (LBA)
/dev/sda5            9117       12160    24450898+   7  HPFS/NTFS
/dev/sda6            2624        2866     1951834+  82  Linux swap / Solaris
/dev/sda7            2867        9116    50203093+  83  Linux

Partition table entries are not in disk order

```

And my menu.lst file:
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=0fb8b4e2-dbfa-423e-ad4e-9a531ad7df4c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0fb8b4e2-dbfa-423e-ad4e-9a531ad7df4c ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0fb8b4e2-dbfa-423e-ad4e-9a531ad7df4c ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0fb8b4e2-dbfa-423e-ad4e-9a531ad7df4c ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0fb8b4e2-dbfa-423e-ad4e-9a531ad7df4c ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet


title		Windows XP Professional
map		(hd0)(hd1)
map		(hd1)(hd0)
root		(hd1,0)
savedefault
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I'm assuming that I should have put the XP entry before ### BEGIN AUTOMAGIC KERNELS LIST instead of where I've posted it.

In case it helps, I removed the vista partition through XP before I installed it. I learned from the last time on a different comp that Vista partitions can't be resized in the install.

So, if anyone could tell me what hdd location I should be addressing Xp as, it would be greatly appreciated.

Cheers
Hoges

---

### Post by Inxsible on 2007-06-15
'fraid I don't see a boot drive for XP. But it seems its probably your sda1.

Boot up with the Live Cd and go to the terminal and do this to repair it.

```
sudo fsck /dev/sda1
```

your menu.lst entryy should be (hd0,0) = first hard drive, 1st partition. (Assuming that sda1 IS your XP boot partition)

---

### Post by confused57 on 2007-06-15
Since you only have one hard drive, you don't need the mapping lines, Window's on sda5 would have an entry similar to this:
```
title  Windows
root  (hd0,4)
savedefault 
makeactive
chainloader +1
```

Sometimes it can be difficult to boot Windows installed on a logical partition...hopefully, this entry will boot your XP.

---

### Post by hoges on 2007-06-15
> **confused57 said:**
> Since you only have one hard drive, you don't need the mapping lines, Window's on sda5 would have an entry similar to this:
```
title  Windows
root  (hd0,4)
savedefault 
makeactive
chainloader +1
```

Sometimes it can be difficult to boot Windows installed on a logical partition...hopefully, this entry will boot your XP.

Ok, grub didn't like this one. Came up was "invalid boot device". It's definitely sda5, because it's mounted under ubuntu and showing everything in it.

I'm just going to give the live cd a show now, if I can find the disk...

---

### Post by hoges on 2007-06-15
hmmm....

```
fsck 1.40-WIP (14-Nov-2006)
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda5

```

same for sda1, etc.

I'm really confused. I know it's actually there, it just doesn't want to boot from it...

I guess I could always reinstall it, but that takes forever, and it also means I have to fix ubuntu again anyway.

If it helps a all, sda1 seems to be an 8mb gap on the drive that vista kind of stuck on there, and there's also a toshiba partition in there somewhere too. I'm not too sure what that's there for, 'cause I already have a dvd that came with the lappy. The fat32 is one that I made during ubuntu installation to dump files on so I can see them in xp. XP's going to be a secondary os for software I can't run on ubuntu. I don't need it for a month or so, but would still like to get it working...

So somebody said that it was a logical drive. Any idea how I can change it back to a primary?

EDIT: Or rather, any more ideas on how to get it working???

I'm beginning to think this wasn't a noobish this after all...

---

### Post by confused57 on 2007-06-15
> **hoges said:**
> hmmm....

```
fsck 1.40-WIP (14-Nov-2006)
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda5

```

same for sda1, etc.

I'm really confused. I know it's actually there, it just doesn't want to boot from it...

I guess I could always reinstall it, but that takes forever, and it also means I have to fix ubuntu again anyway.

If it helps a all, sda1 seems to be an 8mb gap on the drive that vista kind of stuck on there, and there's also a toshiba partition in there somewhere too. I'm not too sure what that's there for, 'cause I already have a dvd that came with the lappy. The fat32 is one that I made during ubuntu installation to dump files on so I can see them in xp. XP's going to be a secondary os for software I can't run on ubuntu. I don't need it for a month or so, but would still like to get it working...

So somebody said that it was a logical drive. Any idea how I can change it back to a primary?

One other thing you could try is to turn the boot flag on for your Window's partition...you can probably do it with gparted, or the gparted live cd:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Inxsible on 2007-06-15
confused57 is right, your windows is probably on sda5, on sda1 the id is 27 -- dont know what that is. NTFS id is always 7, 83 for linux and 82 for swap. I guess its just some unallocated space on sda1 or more likely a recovery partition.

---

### Post by Inxsible on 2007-06-15
Its always a better idea to have Windows on its on primary partition. :(
 
I know ....it sucks !!

---

### Post by hoges on 2007-06-15
The stupid thing is that it *was* on it's own primary partition!!! I don't know, but maybe somehow i changed it when I installed ubuntu???

sda1 is some random 8mb space vista installed - no idea what it's for, but it was at the beginning of the drive, so I didn't risk removing it.

This is insane! The gparted flag didn't work, all it comes up with is "invalid boot device". It definitely was primary partition before I installed it, so there must be some way to change it back.

OK, just checked gparted to double check partitioning. sda5,6,7 are xp, swap, ubuntu respectively as logical partitions under sda3. There are some random unallocated spaces, sda1 is the toshiba backup at around 1.33gb,  sda2 is a spare fat32 partition I made during the ubuntu installation.

All I can think of is that during the ubuntu installation, the partition manager merged the xp with the linux ones.

There are currently only 3 primary partitions, so I think there can be 4 max.

Does anyone know of any way to convert sda5 to it's own primary partition? I can't see any option under gparted?

---

### Post by hoges on 2007-06-16
thinkinf of doing fixmbr under xp install disk to see if xp will boot of it's own boot record, then if that works reinstall grub.

Nobody has any other ideas?

---

