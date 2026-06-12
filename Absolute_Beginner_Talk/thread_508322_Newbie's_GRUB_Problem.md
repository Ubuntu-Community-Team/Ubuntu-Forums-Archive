---
title: "Newbie's GRUB Problem"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by DevgruSeal on 2007-07-24
There seems to be this thing with GRUB and me. It doesn't like me. I don't like it because it doesn't like me.

I haven't used Ubuntu in ages. I decided to boot it up again (I'm on a dual-boot XP system), and cannot get to it anymore, for I have "Error 17: Could not mount the selected partition".

I've been Googling for around 2-3 hours now, and I'm not getting anywhere.

Here's my setup:
I have 3 hard-drives.
PATA + 2 SATA.

I take it the order is (As my BIOS lists them vertically on different rows as is here, just no numbering scheme):
80gb (SATA; NTFS; Windows XP) = hd0 (or aka /dev/sda1?)
160gb (PATA; NTFS; Storage) = hd1 (or aka /dev/hda1?)
250gb (SATA; Partitioned: See below) = hd2 (or aka /dev/sdb1../dev/sdb2..etc?)

The 250gb hard-drive contains these partitions:
1st partition (hd2,0..Right?) = Ubuntu (Ext3)
2nd partition (hd2,1..?) = Used to be for Vista testing, but is now formatted for NTFS
3rd partition = SWAP
4th partition = NTFS Storage

When trying to type **any** find command at the GRUB console (Using the Ubu LiveCD Terminal), I recieve Error 15: File not found.

At the same terminal, "gemoetry (hd0)" returns Error 21: Selected disk does not exist.
As does "root (hd2,0)".
As well as "find /boot/grub/menu.lst".

fdisk -l:
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2611    20972826   83  Linux
/dev/sdb2            2612        5222    20971520    7  HPFS/NTFS
/dev/sdb3            5223        5483     2096482+  82  Linux swap / Solaris
/dev/sdb4            5484       30401   200153835    7  HPFS/NTFS

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19457   156288321    7  HPFS/NTFS

```

So far I've tried:
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)
But it wouldn't allow me to continue without allowing it to format, which isn't ideal right now.

Suggestions? This is tiring. :\

---

### Post by AceofSpades19 on 2007-07-24
could you boot up a livecd like KNOPPIX and navigate to your harddrive and post your menu.lst?

---

### Post by DevgruSeal on 2007-07-24
Certainly. I'm using a second computer to the side and am on a Ubuntu LiveCD on my main system.

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
# kopt=root=UUID=1ab1277f-542f-4de9-bc3e-819c482bf0d1 ro
# kopt_2_6=root=/dev/sdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sdb1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

### Post by AceofSpades19 on 2007-07-24
have you tried reinstalling grub?

---

### Post by DevgruSeal on 2007-07-24
I'd give it a try depending on what (possible?) consequence/risk there is, but I don't know how to go about doing it anyway :x

I also tried this, by the way:
sudo mkdir /media/ubuntu
sudo mount /dev/sdb1 /media/ubuntu
sudo chroot /media/ubuntu
sudo grub-install /media/ubuntu

With no success -- It just kept giving me the help read-out. Then I tried "sudo grub-install /dev/sdb1" instead, and it returned:
/dev/sdb1: Not found or not a block device.

---

### Post by DevgruSeal on 2007-07-24
Also, I've just tried [this](http://ubuntuforums.org/showthread.php?t=224351), but it didn't fix the problem.

The method I tried (Because it can't find the drives otherwise) was Tosk's

---

### Post by DevgruSeal on 2007-07-24
Sorry for a bump, but please help :(

---

### Post by tomcheng76 on 2007-07-24
it means that hd2,0 is acturally not a Linux partition

do you change the plug postion of SATA?

i remember i use the following command to fix grub, but i use fedora DVD...

# chroot /mnt/sysimage

# grub-install <devive> (/dev/sdb1 may be, fedora will do a harddisks scan)

---

### Post by DevgruSeal on 2007-07-24
I've not changed their plug positions. The only thing new in hardware is an IDE DVD burner as secondary slave.

---

### Post by tomcheng76 on 2007-07-24
i have a stupid idea, it should not hurt your filesystem,
if u are luck, you should able to boot ubuntu by trying it few times

just change "(hd2,0)" to (hd3,0) inside the menu.lst

if it doesnt work, change it to hd4,0 or even hd0,0

---

### Post by DevgruSeal on 2007-07-24
I tried multiple times using (hd3,0) but I've not tried other variations. I'll try it and see what happens.

---

### Post by tomcheng76 on 2007-07-24
btw
i noticed that you said
At the same terminal, "gemoetry (hd0)" returns Error 21: Selected disk does not exist.
As does "root (hd2,0)".
As well as "find /boot/grub/menu.lst".

Did you run grub as a root ?
i mean using "sudo grub" instead of grub
before you type "geometry (hd0)"

---

### Post by DevgruSeal on 2007-07-24
:\
(hd0,0) works...
Why does this work when (hd0,0) is my XP drive?

Ahh, maybe its because to boot up, I use my BIOS's Boot Menu, then select the drive Ubuntu is on, which then makes it hd0,0? As such the 2nd partition would be hd0,1, I guess.

If GRUB were on my XP drive, the first drive, then that's when hd2,0 would be it's name?

---

### Post by tomcheng76 on 2007-07-24
noticed that XP is acturally on hd1
it does a swap b4 use the chainloader
as i remembered that chainloader (NTbootloader) for some reason have to be hd0 ~~"
plz do a google search if u really want to know, i just simply skiped them

---

### Post by DevgruSeal on 2007-07-24
Ah OK. What're these two 'map' commands at the end of the WinXP boot sequence in menu.lst? I've taken it to understand it is a 'switch'.

---

### Post by asmoore82 on 2007-07-24
aha!! yes... almost all these new BIOSes that let you pick a hard drive to boot from do so by logically switching it to hd0 ... a trick that GRUB used to use to boot stubborn Windows with the 'map' statements

---

### Post by MQMike on 2007-07-25
Try putting the root (hd1, 0) * after * the map commands.
Try rootnoverify (hd1, 0) instead of root (hd1, 0).

title XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1, 0)   # or just root (hd1, 0)
makeactive     # this may be optional?
chainloader +1

(Windows likes to be on the first (BIOS-) bootable hard drive, first partition.
The map commands fool Windows into thinking it is on (hd0).
map (hd0) (hd1)
says map (hd1) to (hd0), so when you "see" hd1, make a virtual switch and replace it with hd0 (nothing happens physically).  (Don't worry about the second map statement, that's another story.  Sometimes I leave it out.))

GRUB sees your hard drives the same way BIOS sees them (enumeration-wise).
Linux may see things differently (and that's ok, we just need to know what's what).

---

