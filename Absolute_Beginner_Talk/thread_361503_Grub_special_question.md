---
title: "Grub special question"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by regiszt on 2007-02-14
Hi,
I have a problem which may be solved in this forum. I installed ubuntu Edgy 6.10 several days ago to my primaryslave harddisk. When I installed, my primarymaster harddisk was removed. So the whole system works fine but I can't boot from my primarymaster harddisk from the grub menu. Here is the list about my drives and op. systems:
PriMaster Xp                                   
PriSlave Ubuntu hd(0,1)                   It's okay
SecMaster DvD                              
SecSlave Xp2 hd(2,0)                      It's okay

I don't want to change anything on my primarymaster, so how can I solve this problem because the default harddisk is the hd(0,0) in grub but I need hd(-1,0) :) to boot which is impossible.

Thank you in advance !!!!!!

---

### Post by LotsOfPhil on 2007-02-14
I don't fully understand. 

Which one can you boot, Ubuntu or XP?
What do you mean by needing hd(-1,0)?

Please post the output from:
```
sudo cat /boot/grub/menu.lst
```

---

### Post by dannyboy79 on 2007-02-14
WOW, that was the totally wrong thing to do. The easiest thing to do is going to be just either reinstall ubuntu and this time LEAVE the primary master there. or you'll have to mess around with your device.map and menu.lst files located within /boot/grub/

ok, so it appears that you're telling me that your bios is booting your primary slave which boots linux right away without giving you an option to boot winxp correct? if so, we need to see some things. please post the output from these 2 files.

/boot/grub/menu.lst

and 

/boot/grub/device.map

then I can help ya.

---

### Post by regiszt on 2007-02-14
Sorry for the desinformation but I took apart my machine and checked the harddiscs' order, so when I installed the ubuntu then my secondaryslave wasn't there as you can see here:

PriMaster Xp       hd(1,0) and hd(2,0)       both setup start this Xp
PriSlave Ubuntu hd(0,1) It's okay
SecMaster DvD
SecSlave Xp2  

The device.map file contains: (hd0)   /dev/hdb
The menu.lst file contains:

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
color cyan/blue white/blue

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
# kopt=root=UUID=d858e502-1111-4a26-bdcc-02d5709bf0a8 ro
# kopt_2_6=root=/dev/hdb2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
# defoptions=quiet splash locale=hu_HU

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

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hdb2 ro quiet splash locale=hu_HU
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb2 ro quiet splash locale=hu_HU
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Professional - magyar
root		(hd1,0)
savedefault
makeactive
chainloader	+1

title		Microsoft Windows XP Professional - 2
root		(hd2,0)
savedefault
makeactive
chainloader	+1

In this case both xp start PrimaryMaster !!!!!!!
When I boot , I choose the PrimarySecondary from the bios boot menu for linux  or SecondaySlave if I would like to start Xp2.

---

### Post by dannyboy79 on 2007-02-14
ok, well it doesn't sound like you're even using grub??? you shouldn't be messing with your hard disk boot order so that you get different os to boot, thats what the grub boot loader is for. so please post the output from sudo fdisk -l and also inform me where your hard drives will be positioned for good in the bios. then I can help you. also, inform me what mbr grub overwrote, did it overwrite the primarymaster's mbr?

or if  you think you can figure it out, here ya go: [http://www.ubuntuforums.org/showthread.php?t=220452](http://www.ubuntuforums.org/showthread.php?t=220452)

---

### Post by regiszt on 2007-02-16
Here is the sudo fdisk -l result:

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cilinderek of 16065 * 512 = 8225280 bytes


  Eszköz Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1912    15358108+   c  W95 FAT32 (LBA)
/dev/hda2            1913        9561    61440592+   7  HPFS/NTFS
/dev/hda3            9562        9964     3237097+   c  W95 FAT32 (LBA)

Disk /dev/hdb: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cilinderek of 16065 * 512 = 8225280 bytes

  Eszköz Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/hdb2            2551        4661    16956607+  83  Linux
/dev/hdb3            4662        4865     1638630   82  Linux swap / Solaris

Disk /dev/hdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cilinderek of 16065 * 512 = 8225280 bytes

  Eszköz Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        4865    39078081    7  HPFS/NTFS

---

### Post by regiszt on 2007-02-16
Anyway I choose primarysecondary from my bios's boot list menu.

---

### Post by dannyboy79 on 2007-02-16
well there is 2 things you can do, since you are able to boot into grub and are currently able to chose the primarymaster winxp install or linux, then you can simply modify the boot.ini file within the primarymaster winxp install so that when that starts to boot, it'll ask you from there which windows install you want to boot. you can read about that here
[http://support.microsoft.com/default.aspx?scid=kb;EN-US;q289022](http://support.microsoft.com/default.aspx?scid=kb;EN-US;q289022)


OR


well here, try this: [http://www.linuxforums.org/forum/installation/66476-howto-multiple-independent-winxp-installs-same-harddrive-via-grub.html](http://www.linuxforums.org/forum/installation/66476-howto-multiple-independent-winxp-installs-same-harddrive-via-grub.html)

it talks about having to hide the windows installs from each other. there is a great thread  about booting 100+ os's from 1 grub floppy. ([http://www.justlinux.com/forum/showthread.php?threadid=143973](http://www.justlinux.com/forum/showthread.php?threadid=143973)) and here is an example of 1 of his winxp pro's being booted from a seperate hard drive.

# Third disk sda is a Sata with 15 partitions, 9 are bootable

title          XP pro @ sdb1
hide           (hd0,0)
hide           (hd1,0)
hide           (hd1,1)
unhide         (hd2,0)
map            (hd2) (hd0)
map            (hd0) (hd2)
root           (hd2,0)
makeactive
chainloader    +1

---

