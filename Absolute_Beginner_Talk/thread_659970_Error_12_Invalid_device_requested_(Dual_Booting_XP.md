---
title: "Error 12: Invalid device requested (Dual Booting XP and Ubuntu)"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by mrducky34 on 2008-01-06
I have searched the forums, but I have not found any solutions. Well, here is my problem:
I start up my computer and it gives me the list of OS's. I can run all Ubuntu ones just fine, but when I try to use Windows XP it gives me Error 12. Here are the specs for my computer:

Dell Inspiron 1520
Intel Core2 Duo @ 2.00ghz
Nvidia GeForce 8400M GS
2 GB Ram
320gb hard drive

If you need any more info, please tell me.

Here is sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38157   306496071   83  Linux
/dev/sda2           38158       38421     2120580    5  Extended
/dev/sda3   *       38422       38913     3951990   83  Linux
/dev/sda5           38158       38391     1879573+  82  Linux swap / Solaris
/dev/sda6           38392       38421      240943+  82  Linux swap / Solaris

Disk /dev/sdb: 2047 MB, 2047678976 bytes
64 heads, 63 sectors/track, 991 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         991     1997733+   6  FAT16

Disk /dev/sdc: 513 MB, 513802240 bytes
16 heads, 32 sectors/track, 1960 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1960      501744    e  W95 FAT16 (LBA)

Disk /dev/mmcblk0: 252 MB, 252968960 bytes
16 heads, 32 sectors/track, 965 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *           1         965      246989+   6  FAT16

I am trying to dual boot on a single hard drive. If anybody could please help me out, I've tried everything I could.

---

### Post by stump138 on 2008-01-06
can you post the contents of /boot/grub/menu.lst please?

---

### Post by mrducky34 on 2008-01-06
Sure. Here is menu.lst

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
# kopt=root=UUID=de2f00dd-5c79-4ffe-9f7f-0a5667abda96 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=de2f00dd-5c79-4ffe-9f7f-0a5667abda96 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=de2f00dd-5c79-4ffe-9f7f-0a5667abda96 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by stump138 on 2008-01-06
> **mrducky34 said:**
> 

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


Looks like windows is showing in the wrong place.  make a backup of your /boot/grub/menu.lst and change the line:

root (hd0,1) from above to root(hd0,0) and give that a whirl.  Good Luck:)

---

### Post by mrducky34 on 2008-01-06
I shall try that, thanks

---

### Post by mrducky34 on 2008-01-06
So far, no good. It just says 

Starting up...

Loading DRMK Version 8.00...

It just says that for a while. Should I keep waiting?

---

### Post by mrducky34 on 2008-01-06
No good. It never finishes loading. Any more advice? I'm at a total loss at what to do here

---

### Post by stump138 on 2008-01-06
something that troubles me is the fact that when you do a fdisk -l you don't show any NTFS partitions.  Is your winxp different hard drive that is not formatted ntfs?  If so, change the line (hd0,0) in the windows section to (hd1,0).  The (hdx,y) refers to x=hard disk # and y = partition #.  You might have to try a few different attempts to get it right :)

---

### Post by mrducky34 on 2008-01-06
Alright, I'll tell you what I get

---

### Post by mrducky34 on 2008-01-06
No good. It says 

Invalid system Disk
Replace the disk, and then press any key.

Remember, this is only on one hard drive. 

This is so frustrating. Is there a way to get rid of ubuntu, like preform a system restore without going on windows? 

[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)
That's the original guide I followed, if that helps any

---

### Post by bumanie on 2008-01-06
I agree with stump138,if you are trying to boot buntu and xp off the one hdd,there is no indication that xp is even loaded, ie no ntfs partition. Is it possible that xp has becopme caught in the extended partition? If so, windows will not boot from anything other than a primary partition and it is always suggested that in a dual boot system, it is best to have windows occupying the front section of the hard drive.
Do you have a gparted cd?

---

### Post by stump138 on 2008-01-06
during your install proceudre, did you do a "re-size" or a "guided using the entire drive"?  It appears at a glance here that you may have wiped out windows during your install procedure :(

---

### Post by mrducky34 on 2008-01-06
I recall doing a resize, but oh well. Stupid me, I forgot to back up any of my data. Oh well, It was a pretty new laptop and didn't have any of my personal things on it. I'm just wiping everything clean and reinstalling Windows XP. Can someone point me to a guide with lists step by step instructions on dual booting xp and ubuntu on a single hard drive? The ones I've found are either outdated or are meant for 2 hard drives.

---

