---
title: "Installing on External Hard Drive with Text Mode Iso"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Pete_Misik on 2007-06-23
I'm completely lost and hope that someone can help.  I went through the whole thing of downloading both the LiveCD and the alternate text based install.  The live CD had a problem configuring my external HDD (WD1600JB Media Center).  It said that it could make the partition necessary to install the operating system.  

So, I went with plan b.  Downloaded the alternate install cd and ran it.   I didn't have any problems getting that to install.  When it came to setting up the grub, that took a minute to figure out, but I finally put it in the right spot.

The trouble came when I booted the external HDD, it came back and said ERROR 17: Cannont Mount Selected Drive.

Someone please help.

Thanks.

-Pete

---

### Post by annda on 2007-06-23
first, congratulations! second, can you boot from the live CD and copy&paste the file
/boot/grub/menu.lst
from your **external** hdd?

also, open the terminal and try to identify what device your ext. hdd is:

```
sudo fdisk -l
```

it should be something like /dev/sdb1 - and it should be the same in the grub file.

check out this link on how to repair grub using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

there is a recent thread with useful instructions that you have probably already noticed
[http://ubuntuforums.org/showthread.php?t=457015](http://ubuntuforums.org/showthread.php?t=457015)

UPDATE: to which drive have you installed grub?

---

### Post by Pete_Misik on 2007-06-23
Okay, color me green in this department.  I performed the following and this is what I got back.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2              10        1315    10485760    7  HPFS/NTFS
/dev/sda3   *        1315        7296    48045056    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9702    77931283+  83  Linux
/dev/sdb2           18798       19457     5301450    5  Extended
/dev/sdb3   *        9703       18797    73055587+  83  Linux
/dev/sdb5           19128       19457     2650693+  82  Linux swap / Solaris
/dev/sdb6           18798       19127     2650662   82  Linux swap / Solaris


/dev/sdb is my external drive.  I want to say that sdb3 is where the install is.  I needed to keep a little left on the drive for other storage.  

Can someone leave me step by step on how to boot my drive?

Thanks a million.

-Pete

---

### Post by annda on 2007-06-23
how about the menu.lst file? it's important because it will tell us what grub is trying to boot from and maybe why you are getting grub errors.

besides, you seem to have an unconventional partitioning scheme - i'm no expert but it looks like you have 2 linux installations, complete with 2 swap partitions. is that intended or is it a botched install?

---

### Post by Pete_Misik on 2007-06-23
I think it was a botched install.  I'm going to download GPARTED and knock everything down and start again.  I'll post as soon as I get something new.

Thanks for the wonderful help.

-Pete

---

### Post by Pete_Misik on 2007-06-23
Whew...  What a night this is turning in to.  I scrubbed the whole thing again, re-wiped my external drive, repartitioned it, and did a fresh install.  I got back in to the grub installer and boom, I hit the wall again.  It gave me the unable to mount the drive.  Oh what fun.

Here's the latest sudo fdisk -l

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2              10        1315    10485760    7  HPFS/NTFS
/dev/sda3   *        1315        7296    48045056    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9586    76999513+   b  W95 FAT32
/dev/sdb2            9587       19166    76951350    b  W95 FAT32
/dev/sdb3   *       19167       19436     2168775   83  Linux
/dev/sdb4           19437       19457      168682+   5  Extended
/dev/sdb5           19437       19457      168651   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 


Here's what I have for the /media/disk-1/boot/grub/ menu.lst file.

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
# kopt=root=UUID=5a0d21a7-0cc2-4fa3-9ee8-8a8430139004 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5a0d21a7-0cc2-4fa3-9ee8-8a8430139004 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5a0d21a7-0cc2-4fa3-9ee8-8a8430139004 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
chainloader	+1


Please tell me what I'm doing wrong.

Thanks for the help.

-Pete

---

### Post by logos34 on 2007-06-23
so you're booting to the external usb drive when you get the error?  And you can swtich the Bios boot order and boot windows on the other drive fine?

---

### Post by logos34 on 2007-06-23
And did you install grub to the MBR or root partition of the external usb drive?  If the latter and you're booting to the usb drive and nothing, not even the grub menu is coming up, you could try using the alt install cd to 'repair a broken system', go into the rescue mode menu and choose 'reinstall Grub' and make sure that it goes to the MBR of the external drive -- on the line you would type **'/dev/sdb**'. 

[Read this]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17") and download SuperGrub cd.

---

### Post by Pete_Misik on 2007-06-23
> **logos34 said:**
> so you're booting to the external usb drive when you get the error?  And you can swtich the Bios boot order and boot windows on the other drive fine?

Yeah, it's when I boot the USB drive.  I can boot windows fine.  I just want to put Ubuntu on the external drive and use it all of the time.  My wife is a major windows junkie, so she won't even look at Ubuntu.  

I'll try the option of the broken system and see if that comes up.  I'll leave a post.

Thanks for your help.

-Pete

---

### Post by confused57 on 2007-06-23
> **Pete_Misik said:**
> Yeah, it's when I boot the USB drive.  I can boot windows fine.  I just want to put Ubuntu on the external drive and use it all of the time.  My wife is a major windows junkie, so she won't even look at Ubuntu.  

I'll try the option of the broken system and see if that comes up.  I'll leave a post.

Thanks for your help.

-Pete
If you get a grub boot menu when you boot first to your external drive, highlight your Ubuntu entry, press "e" to edit, then change root from (hd1,2) to (hd0,2), then press "b" to boot....if this works, it's temporary and can be made permanent in your /boot/grub/menu.lst.

---

### Post by Pete_Misik on 2007-06-23
Thanks Confused57, but it didn't work.  I scrubbed the HDD for the 1,000,000th time, but I'm still not having luck.  Before, I was trying to install it on a seperate partition, but this last time, I just went ahead and tried to install it on the whole drive.

Formatted it, reinstalled it, pointed the grub to the directory (I wrote it down when it was installing), and it came back and it said "Cannot mount selected partition".  :(

I don't know what's going on with it.

Are there any other tricks that I can try?

Thanks.

-Pete

---

### Post by confused57 on 2007-06-23
> **Pete_Misik said:**
> Thanks Confused57, but it didn't work.  I scrubbed the HDD for the 1,000,000th time, but I'm still not having luck.  Before, I was trying to install it on a seperate partition, but this last time, I just went ahead and tried to install it on the whole drive.

Formatted it, reinstalled it, pointed the grub to the directory (I wrote it down when it was installing), and it came back and it said "Cannot mount selected partition".  :(

I don't know what's going on with it.

Are there any other tricks that I can try?

Thanks.

-Pete
I would suggest burning a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's only a 5-7 Mb download...boot your pc with SGD & see if it can boot Ubuntu on your external drive.

---

