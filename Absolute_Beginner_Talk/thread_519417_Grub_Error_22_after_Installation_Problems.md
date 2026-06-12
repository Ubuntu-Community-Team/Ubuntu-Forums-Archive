---
title: "Grub Error 22 after Installation Problems"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by stuart264 on 2007-08-07
Ok bit of a long story this, though being experienced with Windows I decided to try Unbuntu on an old IDE drive. So I am good with Windows and a Newbie to Linux 

My initial setup was with an empty 40gb Hard Drive on an IDE connection and my Windows installation on a 200gb SATA Raid drive. Installation went ok until I rebooted unbuntu loaded and Windows didnt, after much looking around online I managed to track it down to a mistake I made during installation where I let the install disk over write / modify the MBR on the SATA raid drive and I have managed to recover this mistake using a combination of the Super Grub Disk and Windows Recovery Console and right now my Windows Installation boots fine if I specify the Windows drive as the boot device on in the bios and my Ubuntu boots fine if I specify the Ubuntu drive in the Bios.

The problem is this when I boot from the IDE Drive (Unbuntu) the Grub loader fires up and gives me a choice of boot choices, when I select the Windows drive I get an "Error 22 No Such Partition", now I am guessing that as I can boot from each driver seperatly there is nothing wrong with the drives themselves the error is that the Grub Loader has a wrong setting in its menu choices but I am too new to Linux to know how to fix it and I would like to get a working system back where I can have the choice to boot Windows or Ubuntu without having to swap the boot device options in the Bios

All help  appreciated but please keep it simple on the Linux side, while I do learn pretty quickly I have only been using Linux now for 48 hours

Stuart.

---

### Post by Inxsible on 2007-08-07
you probably disconnected the Windows drive when you installed Ubuntu and so it wasn't able to recognize where Windows was installed.

post the output of the following

```
df -h
``` ```
sudo fdisk -l
```-l is lowercase L. We will need to then change the menu.lst to reflect the correct drive and partition where windows is.

---

### Post by stuart264 on 2007-08-07
df-h generates the following:-

Filesystem            Size Used Avail Use% Mounted on
/dev/hdd1              36G  3.5G   30G  11% /
varrun                760M  100K  760M   1% /var/run
varlock               760M     0  760M   0% /var/lock
procbususb            760M  128K  760M   1% /proc/bus/usb
udev                  760M  128K  760M   1% /dev
devshm                760M     0  760M   0% /dev/shm
lrm                   760M   33M  727M   5% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1             187G  112G   75G  60% /media/sda1

sudo fdisk -l generates the following:-

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/hdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        4660    37431418+  83  Linux
/dev/hdd2            4661        4865     1646662+   5  Extended
/dev/hdd5            4661        4865     1646631   82  Linux swap / Solaris

---

### Post by stuart264 on 2007-08-07
Hi Inxessible (or anyone) how do I fix this?

---

### Post by Inxsible on 2007-08-07
I am sorry, I should have asked you this earlier. you will need to also post your menu.lst

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by stuart264 on 2007-08-09
Sorry for the delay, pasted below.

Stuart.

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
# kopt=root=UUID=fe46e5c6-e4b1-47e7-9c4c-d01a40a931ba ro

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fe46e5c6-e4b1-47e7-9c4c-d01a40a931ba ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fe46e5c6-e4b1-47e7-9c4c-d01a40a931ba ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=fe46e5c6-e4b1-47e7-9c4c-d01a40a931ba ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=fe46e5c6-e4b1-47e7-9c4c-d01a40a931ba ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition (on Volume 1)
root		(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by stuart264 on 2007-08-09
Updated command lines as since I posted the first lot I have added a 500gb hard drive to my system

Filesystem            Size Used Avail Use% Mounted on
/dev/hdd1              36G  3.5G   30G  11% /
varrun                760M  100K  760M   1% /var/run
varlock               760M     0  760M   0% /var/lock
procbususb            760M  140K  760M   1% /proc/bus/usb
udev                  760M  140K  760M   1% /dev
devshm                760M     0  760M   0% /dev/shm
lrm                   760M   33M  727M   5% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1             466G   77G  389G  17% /media/sda1

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401    7  HPFS/NTFS

Disk /dev/hdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        4660    37431418+  83  Linux
/dev/hdd2            4661        4865     1646662+   5  Extended
/dev/hdd5            4661        4865     1646631   82  Linux swap / Solaris

---

### Post by stuart264 on 2007-08-10
** Bump **

---

### Post by stuart264 on 2007-08-12
Bump....Anyone know how to fix this because I dont?

---

### Post by stuart264 on 2007-08-15
Bump.......help!, still cant fix this :(

---

### Post by stuart264 on 2007-08-19
Help........anyone?

---

### Post by philinux on 2007-08-19
From what I've read this is probably a windows problem. If it's XP you need to ...
Boot with XP cd into rescue mode or whatever they call it. Then I believe there is a program called fixmbr you can use. If this is not helpful, you might look around for some Windows forums and help sites.

---

### Post by petegreenhorn on 2007-08-19
Hi , why not just reinstall Ubuntu , with all the drives connected . It's a fairley quick task and  grub      
will be set up with all drives in the list

---

### Post by stuart264 on 2007-08-19
I was under the assumption from the earlier posts that it just needed a minor edit of the menu.lst file?

---

### Post by petegreenhorn on 2007-08-19
it just seemed to me taking a long time to fix the prob , when it would only take about 30 mins to reinstall the os

---

### Post by stuart264 on 2007-08-19
Issue is I don't really want to muck around with my Windows Installation, the damage the original install did (and I know I did it wrong!) took me 22+ hours runtime to rebuild the drive so it booted and I am really trying to learn linux but not at the expense of fixing drives every time I make an error.

Right now I can boot Ubuntu or Windows by switching the boot drive in the bios, but I really want it to boot the Ubuntu drive, bring up the menu and let me select which OS I boot (preferably with Windows as the timeout default)

---

### Post by jspangler on 2007-08-19
I recommend reinstalling grub from the Live CD. That has fixed Error 22 for me in the past.

Check out this page: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by stuart264 on 2007-08-19
Solved it, I struggled to read through the grub instructions but I finally worked it out after few google searches and looking up various other problems people with SATA and IDE drives had had.

All I needed to change was the menu settings in the grub menu from:-

title Microsoft Windows XP Home Edition (on Volume 1)
root (hd1,1)

To

title Microsoft Windows XP Home Edition (on Volume 1)
root (hd1,0)

Then the Windows OS kicked straight in, I also worked out how to add fancy colours and set it up to boot Windows by default if I dont select ubuntu within 10 seconds.

---

