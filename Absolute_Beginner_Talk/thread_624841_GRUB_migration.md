---
title: "GRUB migration"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by blackice8r on 2007-11-27
I apologize for opening a new thread, but I read the ones I could find and didn't solved my problem, and from what I saw it happened to other people might make ti worse if I don't get it right. 

I am a Linux noob, just installed Ubuntu 7.10 some days ago...
Because I have a laptop and I read that Ubuntu might shorten the life of my laptop's HDD , I installed it on my external usb HDD (I know there is a fix but I am not yet sure if it works correctly).

I have a dual boot Windows xp sp2 + Ubuntu 7.10, all works ok if I have the external HDD plugged , if it is not, then I get an error 21 in Grub, because at install I choose my laptop's HDD to be the place where Grub is installed.
I spent a few days to make some things work in Ubuntu and really really don't have the time now to do it again, so Ubuntu reinstall is last resort.

Since I have a laptop I would like it to be independent of the external HDD, and the solution might be moving GRUB from the laptop the the external HDD so when it is unplugged windows would start, plugged Ubuntu should start, or I should be able to choose.

I've read this article: [http://www.pendrivelinux.com/2007/08/11/grub-error-21-after-full-install-to-usb-hard-drive/](http://www.pendrivelinux.com/2007/08/11/grub-error-21-after-full-install-to-usb-hard-drive/)

I used the commands:

sudo su

fdisk -l

grub-install /dev/sdb3

From "fdisk -l" I get:
--------------------
root@On:/home/raz# fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2032    15361888+   7  HPFS/NTFS
/dev/sda2            2033        7751    43235640    f  W95 Ext'd (LBA)
/dev/sda5            2033        7751    43235608+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xf9a77e3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2168       10836    65537608+   7  HPFS/NTFS
/dev/sdb2           10837       32301   162275400    7  HPFS/NTFS
/dev/sdb3               1        1965    14855368+  83  Linux
/dev/sdb4            1966        2167     1527089    f  W95 Ext'd (LBA)
/dev/sdb5            1966        2167     1527088+  82  Linux swap / Solaris

Partition table entries are not in disk order
-------------------------



Frist time when I was trying: grub-install /dev/sdb3   I was getting an error, unknowin device or something, now I get: 
-----------------------------
Searching for GRUB installation directory ... found: /boot/grub
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sda
(hd1)   /dev/sdb
------------------------------------------------

It looks like it moved it to the external HDD? ...the problem is nothing seems to be changed...I still need the external HDD to be able to book Windows...otherwise I get error 21 in GRUB...

The result from: less /boot/grub/menu.lst

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






Anny Ideea how I can do the migration?

Thank you in advance.

---

### Post by meierfra on 2007-11-27
Step 1:  Fix menu.lst:

```
gksudo  gedit  /boot/grub/menu.lst
```

change

"#groot (hd1,2)" to "#groot (hd0,2)"

(If you want to be able to boot  into windows from the grub-menu, you also need to edit the windows items. Please post your whole "menu.lst" for help.)

Save and close the file. In the terminal:

```
sudo update-grub 
```



Step 2:  Install Grub to the MBR of the external drive:

```
sudo grub  
```

and at the "grub>" prompt

```
root (hd1,2)

setup (hd1)

quit
```


Step 3  Remove grub from the MBR of the internal drive.

If you don't have the "universe" repositories enabled:
Go to Systems-> Adminstration->Software Sources"
Click on the Box next to "Community-maintained Open Source Software (universe)
Click on Close (twice)

Next :

```
sudo apt-get update
sudo apt-get install ms-sys
sudo ms-sys -m /dev/sda

```

Step 4  Reboot with the external drive first in the boot order in the bios.

---

### Post by blackice8r on 2007-12-01
Thank you verry much for your help, finally the problem is sorted.

---

