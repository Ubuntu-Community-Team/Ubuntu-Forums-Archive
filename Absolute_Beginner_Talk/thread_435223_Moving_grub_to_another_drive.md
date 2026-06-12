---
title: "Moving grub to another drive?"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Gorthus on 2007-05-06
Hello all...

I have 2 drives... an IDE 20gb and a SATA 100gb. I have all 3 of my ubuntu partitions (/home, /, and swap) on the 100gb along with a 30gb windows partition... the 20gb was just for backup of some files. Apparently I left it plugged in when installing ubuntu so thats where it installed grub...

How do I move grub to the 100gb so I can take out the 20gb?

---

### Post by Happy_Man on 2007-05-06
Super GRUB!!!!! *cue Superman theme*

---

### Post by cypherzero on 2007-05-06
**$ sudo grub-install --root-directory=/media/drivex /dev/sda**
Replace /media/drivex and /dev/sda accordingly
Or similar

---

### Post by Gorthus on 2007-05-06
> **cypherzero said:**
> **$ sudo grub-install --root-directory=/media/drivex /dev/sda**
Replace /media/drivex and /dev/sda accordingly
Or similar

I don't get it.

---

### Post by aktiwers on 2007-05-06
What is it you dont understand? Try to explain.
I dont know how to do this, but I guess  Cypherzero means you need to type in this command in the Terminal:
```
sudo grub-install --root-directory=**/media/drivex** [B]/dev/sda
```
[/B]Where [B]/media/drivex

[/B]Is your 20gb drive (you need to check the name and replace it.. look in /media/)

And where **/dev/sda **
is your 100gb hard drive. Again change the name to the correct one.

You can view the names of your harddrives (the sda and hda like names)
in fstab.

```
gedit /etc/fstab
```

---

### Post by confused57 on 2007-05-06
> **Gorthus said:**
> Hello all...

I have 2 drives... an IDE 20gb and a SATA 100gb. I have all 3 of my ubuntu partitions (/home, /, and swap) on the 100gb along with a 30gb windows partition... the 20gb was just for backup of some files. Apparently I left it plugged in when installing ubuntu so thats where it installed grub...

How do I move grub to the 100gb so I can take out the 20gb?
You can also use the live cd to install grub to your 100 Gb drive:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
You would do something like this:
```
sudo grub
find /boot/grub/stage1
```
this "should" return...root (hd1,x),  you would then enter:
```
root (hd1,x)
setup (hd1)
quit
```

This should set up grub to your 2nd drive's mbr, set your bios to boot first to this drive, you should get a grub menu at boot...if you do, highlight your Ubuntu entry, press "e", then change root from (hd1,x) to (hd0,x), then press "b" to boot...this change is only temporary, but if it works, you can make it permanent in your /boot/grub/menu.lst.

---

### Post by Gorthus on 2007-05-06
Okay... I got into Ubuntu, but when I try to go into Windows it says NTLDR is missing...

---

### Post by confused57 on 2007-05-06
> **Gorthus said:**
> Okay... I got into Ubuntu, but when I try to go into Windows it says NTLDR is missing...
Boot into Ubuntu and post the ouput of:
```
gedit /boot/grub/menu.lst
```
and
```
gedit /boot/grub/device.map
```

---

### Post by Gorthus on 2007-05-06
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
timeout		10

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
# kopt=root=UUID=14350fc5-bbfc-4680-9069-116f3dbaa875 ro

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=14350fc5-bbfc-4680-9069-116f3dbaa875 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=14350fc5-bbfc-4680-9069-116f3dbaa875 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

```
(hd0)	/dev/sda
(hd1)	/dev/sdb
```

---

### Post by confused57 on 2007-05-06
Your current Window's entry "should" work, you could try "rootnoverify (hd0,0), instead of "root (hd0,0).  Again, you could test this temporarily by highlighting your Window's entry at the boot grub menu, press "e", change to rootnoverify (hd0,0), then press "b" to boot.

You might also want to post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

---

### Post by Gorthus on 2007-05-06
> **confused57 said:**
> Your current Window's entry "should" work, you could try "rootnoverify (hd0,0), instead of "root (hd0,0).  Again, you could test this temporarily by highlighting your Window's entry at the boot grub menu, press "e", change to rootnoverify (hd0,0), then press "b" to boot.

You might also want to post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

```

gorthus@gorthus-desktop:~$ sudo fdisk -l

Disk /dev/sda: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100        6923    14651280   83  Linux
/dev/sda3            6924       12029    41013945   83  Linux
/dev/sda4           12030       12188     1277167+  82  Linux swap / Solaris

```

---

### Post by confused57 on 2007-05-06
I see you've already removed your IDE storage drive...I'm not sure what's going on, but you might try the Super Grub Disk as someone suggested earlier:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's only a few Mb download, but it "should" be able to boot your Windows.

I don't know if commenting your "#(hd1) /dev/sdb"  in your device.map would make a difference or not.

There shouldn't be any way what you've done would have caused your NTLDR to actually be missing, there's just something in your configuration files that needs changing, I'm not sure what.

  You might also post your /etc/fstab:
```
cat /etc/fstab
```

Added:  Here's some info about "NTLDR missing" from the SGD site above:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#NTLDR_is_missing_press_any_key_to](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#NTLDR_is_missing_press_any_key_to)

---

### Post by Gorthus on 2007-05-07
```
gorthus@gorthus-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=14350fc5-bbfc-4680-9069-116f3dbaa875 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb3
UUID=32a01767-5545-4df0-bd2f-5d60602d5204 /home           ext3    defaults        0       2
# /dev/sda2
# /dev/sdb1
# /dev/sdb4
UUID=5b823fe3-4adf-4a68-a569-7a16284196e8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

# Generated by Automatix
/dev/sda1   /media/sda1   ntfs-3g  defaults,locale=en_US.utf8    0    0
## End of Automatix mounted partitions

```

---

### Post by confused57 on 2007-05-07
See Herman's link to "Boot Window's using grub's CLI" in his reply in this thread:
[http://ubuntuforums.org/showthread.php?t=391374&page=4](http://ubuntuforums.org/showthread.php?t=391374&page=4)

Herman also wrote the Super Grub Disk  tutorial that I linked to in my earlier reply.

I suppose you could always try setting up your system back up  with the 20 Gb drive reconnected and see if Window's will boot...might be something to consider as a last resort.

---

