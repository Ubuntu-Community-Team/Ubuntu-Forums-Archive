---
title: "Grub Error for Windows"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by Glass_Onion on 2006-08-29
I've recently had to reinstall Windows on my computer, which worked fine untill I reinstalled Grub to get back into Ubuntu. Now when I tried logging into Windows I kept getting an error message, when checking my menu.lst file I realised that it was linking to the wrong partition so I fixed this. Now Im just getting a flash of some screen and it's going straight back to the Grub menu. 

I tried to fix it according to [this topic](http://www.ubuntuforums.org/showthread.php?t=244874) by replacing the "root" with "rootnoverify" to no luck. 

My menu.lst

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
# kopt=root=/dev/sda5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-26-amd64-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
boot

title		Ubuntu, kernel 2.6.15-23-amd64-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-amd64-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4

title		Microsoft Windows
rootnoverify		(hd0,3)
savedefault
makeactive
chainloader	+1

```

sudo fdisk -l output
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12100    97193218+   5  Extended
/dev/sda2           12101       12361     2096482+  82  Linux swap / Solaris
/dev/sda3           12362       14119    14121135    b  W95 FAT32
/dev/sda4   *       14120       19456    42869452+   7  HPFS/NTFS
/dev/sda5               1        7001    56235469+  83  Linux
/dev/sda6            7002       12100    40957686   83  Linux

```

Can someone help me?

---

### Post by Herman on 2006-08-29
Hello Glass_Onion,
> Now Im just getting a flash of some screen and it's going straight back to the Grub menu.  What screen? Has it got an error message? Something like 'autocheck program not found - skipping autocheck' by any chance, or would it be some other error message?
If it's the autocheck not found it's because you have Windows on a non-first partition (I have a Windows on (hd0,3) as well, and boot.ini needs a little edit to tell it where it is.
You can **    A Birds's eye view of Windows XP **(showing the bootloader files)..................................[GO]("http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP")
And check if the line in your boot.ini file, as shown in fig 6 mbr there, has the right partition number on the line that begins with the word 'default='.
The other line where is has a partition number that may need to be corrected is the line that begins with the word 'multi'.
In that illustraation, the number to be changed is the number right after the word 'partition', (on both lines). As you can see in that illustration, it has number 1 after the word 'partition' on both lines. You would change those both to number 4 instead.
I don't know how you can do that without booting Windows and relaxing the file permissions on that file, you can look at it from Ubuntu, but you can't edit it from Ubuntu. For one reason you  probably don't have the  file permissions relaxed, and  for another, you have NTFS already. 
I could edit mine from Ubuntu because I relaxed it's file permissions while I had Windows  booted and it was FAT32. Then after mine was edited, i converted to NTFS.
First, check and see if that's the problem or not. If it is, you might have to use a GParted LiveCD to  copy and paste Windows around until you make Windows to the partition number it thinks it is, (it usually presumes it's partition number 1). That will probably mean deleting Ubuntu and needing to re-install if afterwards.
This is all just a guess, and it could be wrong, so before I waste more words, I'll wait to hear from you, I'll be back in around 12 hours. There are lots of others here that might be able to help you better than I can anyway though, so if you are lucky enough to have someone jump in with an idea, in the meantime, take it.
Regards, Herman :D

---

