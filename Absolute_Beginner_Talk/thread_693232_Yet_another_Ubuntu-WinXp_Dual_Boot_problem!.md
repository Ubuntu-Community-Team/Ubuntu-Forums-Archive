---
title: "Yet another Ubuntu-WinXp Dual Boot problem!"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by gtzam on 2008-02-10
One more thread on this topic since I couldn't find any answer in the previous posts that worked for me.
I installed Ubuntu 7.10 on the First Partition of my HD, deleting one of the two Winxp partitions that existed before. I have managed to keep the second WinXP partition, which can only be installed from a floppy disk and not from Grub. Therefore it works, the issue is probably with the grub settings. Any suggestion on how to make winxp bootable using Grub? Needless to mention that Ubuntu boots-up without any problems whatsoever...
My HD partitions are as follows:
```

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdb43d6c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         851     6835626   83  Linux
/dev/sda2            2954        4864    15350076    7  HPFS/NTFS
/dev/sda3   *         992        2953    15759733+   7  HPFS/NTFS
/dev/sda4             852         991     1124550    5  Extended
/dev/sda5             852         991     1124518+  82  Linux swap / Solaris

```

And the Grub **menu.lst** file is
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
# WARNING: If you are using dmraid do not use 'savedefault' or your
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
# kopt=root=UUID=22415b4b-0958-4268-bd80-414218327f6e ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=22415b4b-0958-4268-bd80-414218327f6e ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=22415b4b-0958-4268-bd80-414218327f6e ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows NT/2000/XP (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

```

I have tried most of the obvious changes in Grub like roo(0,x) values, rootnoverify, etc.
Any suggestions will be greatly appreciated! :)

---

### Post by spiderbatdad on 2008-02-10
title windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

---

### Post by gtzam on 2008-02-10
Spiderbatdat, thanks for the suggestion. I tried it and got the message that the hd1 did not exist. I only have one HD....

---

### Post by spiderbatdad on 2008-02-10
doh!

title windows XP
root (hd0,1)
makeactive
map (hd0) (hd1)
map (hd0) (hd2)
chainloader +1

???

---

### Post by dstew on 2008-02-10
Do you know for sure that /dev/sda3 is the bootable partition? The boot flag can be set, but maybe /dev/sda2 is really the bootable part. Did you try **rootnoverify (hd0,1)** in the grub menu? You can quickly try different things by pressing 'e' to edit the lines directly from the grub menu when you start up. The changes don't stick, but sometimes it is quicker to debug booting problems that way.

---

### Post by mrsteveman1 on 2008-02-10
Use a windows CD to fix windows booting first. Both the Vista and XP cds can fix their respective OS boot problems, in XP its more complicated but basically boot into the recovery console and run fixboot and fixmbr, then make sure windows boots ok on its own before going on. This step may be necessary if the windows partition boot record is damaged, even if the MBR is fine.

Next boot an ubuntu livecd, change the active partition to your linux partition:

```
sudo parted
set 1 boot on
```

next reinstall grub to your linux partition

```
sudo grub
find /boot/grub/stage1 (just to verify the drive)
root (hd0,0)
setup (hd0,0)
```

Then go edit your menu.lst file and verify the windows entry (Which I'm assuming is sda3 otherwise known as (hd0,2) )


```
sudo nano /boot/grub/menu.lst

Title Windows XP
rootnoverify (hd0,2)
makeactive
chainloader +1
```

---

### Post by gtzam on 2008-02-12
> **spiderbatdad said:**
> doh!

title windows XP
root (hd0,1)
makeactive
map (hd0) (hd1)
map (hd0) (hd2)
chainloader +1

???

Thanks but it didn't work. It returned a String Error Message...

---

### Post by gtzam on 2008-02-12
> **dstew said:**
> Do you know for sure that /dev/sda3 is the bootable partition? The boot flag can be set, but maybe /dev/sda2 is really the bootable part. Did you try **rootnoverify (hd0,1)** in the grub menu? You can quickly try different things by pressing 'e' to edit the lines directly from the grub menu when you start up. The changes don't stick, but sometimes it is quicker to debug booting problems that way.

Thanks for the tip. I had tried that already...

---

### Post by gtzam on 2008-02-12
> **mrsteveman1 said:**
> Use a windows CD to fix windows booting first. Both the Vista and XP cds can fix their respective OS boot problems, in XP its more complicated but basically boot into the recovery console and run fixboot and fixmbr, then make sure windows boots ok on its own before going on. This step may be necessary if the windows partition boot record is damaged, even if the MBR is fine.



Thanks for the thorough answer! I did try Fixmbr and Fixboot from the recovery console on XP and WinXP still could not boot. They are installed on (hd0,2), or driver letter D under the windows terminology of my only HD. I can only boot them from a floppy drive. Any further suggestions are more than welcome!

---

### Post by mrsteveman1 on 2008-02-12
I may have gotten one of those commands wrong, its fdisk /mbr not fixmbr. Fixmbr is another command in the recovery console, but you want fdisk /mbr here. I still think the windows bootloader isn't working correctly, the only way i know of to fix the windows xp boot process is through the recovery console. When you start the recovery console, it should ask you to login to one of the windows installations on the disk. It might say c:\ instead of d:\

Then it should ask for your admin password, Then you run fdisk /mbr which should recover the windows MBR boot code. Then you run fixboot which should rewrite the partition bootloader into the windows partition.



Here are the relevant support articles for these 2 commands:

[Fixmbr]("http://support.microsoft.com/kb/69013")

[Recovery console]("http://support.microsoft.com/kb/314058") (fixboot is near the end)

---

### Post by gtzam on 2008-02-12
> **mrsteveman1 said:**
> 

Here are the relevant support articles for these 2 commands:

[Fixmbr]("http://support.microsoft.com/kb/69013")

[Recovery console]("http://support.microsoft.com/kb/314058") (fixboot is near the end)

&#932;hanks a lot for the additional help. Unfortunately the fdisk /mbr comman does not exist in winXP...Any other ideas?
Thanks

---

### Post by Astra on 2008-02-12
I'm definitely not an expert on Linux so I'll stay out of that part of this.  However, I do have some experience of dual-booting Windows installations (all of them painful).  From all of that, if it was me, I would only ever install the Windows OS to partition 0 of any hard-drive.  Really asking for problems if do anything else, Windows is pretty well hell bent on being on 'C'.

I'd start again install Windows first and only on the first partition of the drive.  However, there are detailed docs on problems in booting  Windows through boot-managers at TeraByte Unlimited.

[http://terabyteunlimited.com/kb/category.php?id=19](http://terabyteunlimited.com/kb/category.php?id=19)
[http://terabyteunlimited.com/kb/category.php?id=20](http://terabyteunlimited.com/kb/category.php?id=20)

Most of the articles are really geared toward using BootIt as a boot manager but some of the inf is of general interest for trying to dual boot anything.

Good luck.

---

### Post by Moop on 2008-02-12
If XP is on d: drive then I would think that you would need to switch to d: in the XP recovery console before using the fixboot or fixmbr command. If I remember you can type help for a list of commands.

---

### Post by mrsteveman1 on 2008-02-12
The windows drive letters have little to do with the partition order on the drive, windows assigns drive letters in the registry based on a few different  (mostly arbitrary). If windows ends up being the D: drive, usually it means when it was installed there was either another installation of windows already present or perhaps another NTFS partition present. 

Windows XP can be installed anywhere on a drive except an extended partition as long as the bootloaders are intact.


For windows to refuse to boot correctly one of a few things are true, either the MBR has bad boot code in it, or the windows partition is not flagged bootable, or the partition boot code is missing, or the windows bootloader itself (ntldr) is missing or corrupted. The recovery console should be able to fix all of these.

Fdisk does not exist IN windows when installed, it only exists in the recovery console on the XP CD. If you can boot into windows you can use the mbrfix program though. It is available [here]("http://www.ambience.sk/experiments/MbrFix.exe").

---

