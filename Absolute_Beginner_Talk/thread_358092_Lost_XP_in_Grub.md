---
title: "Lost XP in Grub"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by HareBall on 2007-02-10
I know this doesn't sound like a big deal, but I lost XP in my GRUB. I need to be able to access XP to print and it doesn't show up anymore. I haven't checked it in about 2 weeks. This morning I tried to reboot and it wasn't there. I have updated my computer just about every morning this week with the updates they have been sending out.
I tried to remove my second drive(Ubuntu) and reboot without it in, but I got an error number 21 I believe. Wouldn't boot at all without my Linux drive in.
I really need to have this access. I have important tax info on that drive and am trying to get it done.:(
I posted this in another forum, but haven't gotten a response.

---

### Post by mikewhatever on 2007-02-10
Hi,
can you please post the output of ```
sudo fdisk -lu
```

---

### Post by HareBall on 2007-02-10
> **mikewhatever said:**
> Hi,
can you please post the output of ```
sudo fdisk -lu
```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       80325   302760989   151340332+   7  HPFS/NTFS
/dev/sda3       302760990   312496379     4867695   db  CP/M / CTOS / ...

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    81915434    40957686   83  Linux
/dev/sdb2       309620745   312576704     1477980    5  Extended
/dev/sdb3        81915435   309620744   113852655   83  Linux
/dev/sdb5       309620808   312576704     1477948+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by mikewhatever on 2007-02-11
It looks like the latest kernel update has also updated your GRUB menu, so that the Windows entry is gone. If you happen to have a backup copy of GRUB menu, you can copy the Windows section only from it to the current menu. The following command will give you the list of files in grub menu directory: ```
ls /boot/grub
```
look for something like this:  menu.lst.backup
If there is no backup copy, we can try editing the menu, so then, can you also post the GRUB menu
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by HareBall on 2007-02-11
> **mikewhatever said:**
> It looks like the latest kernel update has also updated your GRUB menu, so that the Windows entry is gone. If you happen to have a backup copy of GRUB menu, you can copy the Windows section only from it to the current menu. The following command will give you the list of files in grub menu directory: ```
ls /boot/grub
```
look for something like this:  menu.lst.backup
If there is no backup copy, we can try editing the menu, so then, can you also post the GRUB menu
```
sudo gedit /boot/grub/menu.lst
```
I didn't have a backup copy, so here is my GRUB menu:

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
timeout		15

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
# kopt=root=UUID=234db7b6-ba61-414e-9ca2-8e7d94261540 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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
# defoptions=quiet splash vga=769

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

title		Ubuntu, kernel 2.6.17-11-386
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=234db7b6-ba61-414e-9ca2-8e7d94261540 ro quiet splash vga=769
initrd		/boot/initrd.img-2.6.17-11-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=234db7b6-ba61-414e-9ca2-8e7d94261540 ro single
initrd		/boot/initrd.img-2.6.17-11-386
boot

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=234db7b6-ba61-414e-9ca2-8e7d94261540 ro quiet splash vga=769
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=234db7b6-ba61-414e-9ca2-8e7d94261540 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-386
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=234db7b6-ba61-414e-9ca2-8e7d94261540 ro quiet splash vga=769
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=234db7b6-ba61-414e-9ca2-8e7d94261540 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=234db7b6-ba61-414e-9ca2-8e7d94261540 ro quiet splash vga=769
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=234db7b6-ba61-414e-9ca2-8e7d94261540 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=234db7b6-ba61-414e-9ca2-8e7d94261540 ro quiet splash vga=769
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=234db7b6-ba61-414e-9ca2-8e7d94261540 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

I really appreciate the help you are giving me:KS

---

### Post by Gruelius on 2007-02-11
Hey,
Editing the Grub Config file sounds right on, thats what i did a few years ago when i had a problem like that.
As a dirty solution you could try mounting the partition in media somewhere?
NTFS: [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only)
Fat 32:  [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by Gruelius on 2007-02-11
Try changing
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows XP Media Center Edition
root (hd0,1)
savedefault
makeactive
chainloader +1

to

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows XP Media Center Edition
***root (hd1,1)***
savedefault
makeactive
chainloader +1

Im no grub expert but im presuming its the same hard disk windows is on. I guess linux defaulted it back to that, my grub config file looks like that.

neways back up before ya go ahead of course :P

---

### Post by mikewhatever on 2007-02-11
The good news, as you can see, is that the Windows section of the menu is intact and look right. I think the problem may be, that the latest kernel update added 4 new kernels to the menu, and now, not all of the options are showing. First lets back up just in case:
> cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
Then, try editing the following section 
> ## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all
Change the 7 to 13 which is your number of entries. The number is only supposed to count the the Linux kernels, but I have no idea what else it can be. Perhaps they just do not fit into the boot up menu screen and you simply need to scroll down.

---

### Post by mikewhatever on 2007-02-11
> **Gruelius said:**
> Try changing
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows XP Media Center Edition
root (hd0,1)
savedefault
makeactive
chainloader +1

to

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows XP Media Center Edition
***root (hd1,1)***
savedefault
makeactive
chainloader +1

Im no grub expert but im presuming its the same hard disk windows is on. I guess linux defaulted it back to that, my grub config file looks like that.

neways back up before ya go ahead of course :P
Scroll up to see the fdisk output. Windows and Ubuntu are on seperate HDs.

---

### Post by mikewhatever on 2007-02-11
HareBall, can you also post the output of 
> sudo gedit /boot/grub/device.map
This is to check hoe GRUB maps your HDs.

---

### Post by HareBall on 2007-02-11
> **mikewhatever said:**
> HareBall, can you also post the output of 

This is to check hoe GRUB maps your HDs.
Sorry it takes so long to get back to you. I had to work tonight and wasn't able to get to this til now.
Anyway, here is what you asked for.

(hd0)	/dev/sda
(hd1)	/dev/sdb

---

### Post by HareBall on 2007-02-11
This problem is solved. I found that by hitting page down when the GRUB came up Windows Media Edition shows up and I can then get it to boot up.
Thanx for all the help:KS

---

### Post by mikewhatever on 2007-02-12
Excellent :guitar: 
Check out [Herman's GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm") for a lot of useful options. Fro example, you can hide the kernel entries you do not need, so that your boot menu is shorter.

---

### Post by HareBall on 2007-02-12
> **mikewhatever said:**
> Excellent :guitar: 
Check out [Herman's GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm") for a lot of useful options. Fro example, you can hide the kernel entries you do not need, so that your boot menu is shorter.
Thanx, I edited the menu list and now I only have a few of the kernals showing. This in turn made XP show up again.

---

