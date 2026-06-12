---
title: "XP wont boot, NTLDR missing..."
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by PoHandle on 2007-05-11
First off, allow me to introduce myself to this wonderful community.

Unfortunately, my first post is due to a problem I have encountered.  I recently installed Ubuntu 7.04 set up to dual boot on top of Windows XP.  Both are on the same harddrive in different partitions.  When I first booted after the ubuntu installation, I was able to boot Ubuntu fine, but when I would select "Windows XP Media Edition", the screen would go blank for a split second, then return to the grub menu.  I searched around the forums for information and tried using the Super Grub Disk (which was mentioned in many posts) to attempt to fix my XP boot. (I don't have the XP boot CD)  After selecting to fix the windows MBR, upon booting, I received the error message "NTLDR Missing".  Again, back to the forums, but I was unable to find specific information regarding this.  I hope that someone will be able to help me out here.

Here is my fdisk -l output:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1111     8924076    c  W95 FAT32 (LBA)
/dev/sda2   *        1112       22493   171750915    7  HPFS/NTFS
/dev/sda3           22494       30259    62380395   83  Linux
/dev/sda4           30260       30401     1140615   82  Linux swap / Solaris

```

and here is what my /boot/grub/menu.lst contains:

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
default		5

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
# kopt=root=UUID=c35f8042-a5d0-4d52-8e57-78b867847663 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=c35f8042-a5d0-4d52-8e57-78b867847663 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=c35f8042-a5d0-4d52-8e57-78b867847663 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
makeactive
savedefault
chainloader	+1
```
I should mention that "Windows NT/2000/XP" that boots (hd0,0) is my XP recovery partition.

Any help would be greatly appreciated regarding how I can fix the NTLDR error and be able to boot Windows XP.  Thank you.

---

### Post by forestpixie on 2007-05-11
Can you not get a copy of the file from anyone - ntldr isn't computer specific.

I've had same problem more than once  copied it from another pc to c:\ and it booted fine. (in the days before i dual booted) 

Assuming that you can access your windows partitions from inside linux - you should be able to copy it onto the windows root

---

### Post by rygar on 2007-05-11
boot from your windows XP cd.  log into your windows installation.

type "fixboot".  if your xp drive is not c:, type "fixboot x:" wher x: is your drive.

alternatively, you can copy ntldr and command.com from the i386 directory in your windows cd to c:\

best of luck!
jeff

---

### Post by forestpixie on 2007-05-11
If you haven't got the cd 

i found a copy of  ntldr in my winnt\servicepackfiles\i386 folder 

if you can boot into ubuntu you should be able to find the folder

then copy to the root of that partition (which should be the win boot partition)

---

### Post by PoHandle on 2007-05-11
Thank you for your help.  I had figured out that when I installed ubuntu, Grub had overwritten my windows boot, thus corrupting my windows partition.  I used Testdisk to recover that partition, and can now view the filesystem in Ubuntu, but I cannot copy NTLDR from my recovery partition to my windows partition.

```
pohandle@pohandle-desktop:~$ sudo cp /media/sda1/I386/NTLDR /media/HP_PAVILION/NTLDR
cp: cannot create regular file `/media/HP_PAVILION/NTLDR': Read-only file system

```

However, NTLDR seems to already reside in C:\ .  Now I'm really lost.  I'll fiddle around with Super Grub Disk and see what I can do.

Once again, thanks for the help. :)

**Edit: I noticed that when I boot ubuntu, the windows partition "HP_PAVILION" does not appear until I go into Gparted and switch the boot flag to the Ubuntu partition.**

---

### Post by oilchangeguy on 2007-05-11
read this:
[http://support.microsoft.com/search/default.aspx?catalog=LCID%3D1033&1033comm=1&spid=1173&query=NTLDR+missing&pwt=false&title=false&kt=ALL&mdt=0&res=20&ast=1&ast=2&ast=3&ast=4&ast=7&ast=10&ast=12&mode=a&adv=1](http://support.microsoft.com/search/default.aspx?catalog=LCID%3D1033&1033comm=1&spid=1173&query=NTLDR+missing&pwt=false&title=false&kt=ALL&mdt=0&res=20&ast=1&ast=2&ast=3&ast=4&ast=7&ast=10&ast=12&mode=a&adv=1)

---

### Post by rygar on 2007-05-11
your windows boot sector is almost certainly corrupt.  fixboot should work.

if you want to copy ntldr over from your linux boot instead, you're going to have to enable write access for ntfs drives.  go to add/remove programs and search for "ntfs".  install the "ntfs configuration tool"

applications -> system tools -> ntfs configuration tool.  make sure write support is enabled.

you might have to reboot, then try cp again, and it should work.

---

### Post by PoHandle on 2007-05-14
I have tried using the NTFS configuration utility to overwrite NTLDR and various files, but XP still does not load.  I've also tried *chkdsk lf* on my windows partition, but I always get an error at about 80% of the second step (checking indexes).  and scandisk will not scan my windows partition, even using the NTFS4DOS bootdisk.  I suppose all that is left to do is to borrow the XP setup CD from a friend.  If that doesn't work, I suppose I will have to copy my important programs and files to a DVD and reinstall XP.

Thank you all for your help.

---

### Post by oilchangeguy on 2007-05-14
did you read post #6?

---

### Post by PoHandle on 2007-05-14
Yes, I had read several of the articles displayed in that link from post #6.  Most required that I have the Windows XP setup CD, which I do not have.  As I said before, I tried overwriting NTLDR and NTDETECT.COM, but I still received the error message upon booting.  Gparted gives me an error for my windows partition, stating that there is an inconsistency or something, and instructs me to run chkdsk lf.  The error says something about $Bitmap being inconsistent.  From all this, I gather that I should just borrow an XP setup CD from a friend and attempt to run scandisk and fixboot from that.

---

### Post by heartbeat on 2007-05-17
do you need to copy the ntldr file to the windows drive? just on C: where Program Files and Documents and Settings are?

---

