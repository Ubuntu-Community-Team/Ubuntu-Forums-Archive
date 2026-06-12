---
title: "menu.lst is BLANK when ran through terminal"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by Shinagami101 on 2007-08-12
Alright, when i enter the command to edit the menu.lst (Because of an error 17 during GRUB bootup after selecting the Ubuntu version, which if you dont mind could  you explain exactly how to do that also? (Fix the error)
Anyway, when i open up menu.lst through terminal, it shows up completely blank

But when i open it up from the grub file it shows everything normally.

i get this when i enter it.

(gedit:11260): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

And i also need help with restoring my Windows boot, because i accidently put Grub on my internal drive and i want it on my external.


Any help with this?

---

### Post by macogw on 2007-08-12
I think it always does that when you start a gui program with sudo rights in the terminal.  What did you enter exactly?  Did you use just "menu.lst" or "/boot/grub/menu.lst"

---

### Post by Shinagami101 on 2007-08-12
i used:

gedit /boot/grub/menu.lst

*and if it makes any difference im using the Live CD to run it right now.

---

### Post by Arthur Archnix on 2007-08-12
I t would make a difference. Hopefully the live CD mounts your hard drive automatically, since that will make things easier. If it has, you'll find it under /mnt or /media. Do an 'ls' from those directories and see if anything has been mounted already.

For instance, I have a partition called Arch with another OS mounted under /mnt. If I wanted to edit the /boot/grub/menu.list on that partition I would do this:
```
sudo gedit /mnt/arch/boot/grub/menu.lst
```

If nothing is mounted yet try making a mount point under /mnt
```
sudo mkdir /mnt/ubuntu
sudo fdisk -l
```
fdisk will spit out some info for you. If you have one hard-drive with one partition you'll do this:
```
sudo mount -n /dev/sda1 /mnt/ubuntu -o rw
```
then
```
sudo gedit /mnt/ubuntu/boot/grub/menu.lst
```

---

### Post by Shinagami101 on 2007-08-12
ah cool thanks man, that got my drive mounted (Properly lol)

Alright now i need to edit the menu.lst so i get past the "Error 17" when i try to boot Ubuntu, I assume you will need my Fdisk and menu.lst so here they are:

```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        9333    74927160    7  HPFS/NTFS
/dev/sda3            9334        9725     3148740   db  CP/M / CTOS / ...

Disk /dev/sdb: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12001    96398001   83  Linux
/dev/sdb2           12002       12188     1502077+   5  Extended
/dev/sdb5           12002       12188     1502046   82  Linux swap / Solar
```

the sdb is the one im using for Ubuntu (if not obvious with the "Linux" in the system... anywho

menu.lst :

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
# kopt=root=UUID=3fdc6209-78b3-4d88-8110-57936b671313 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3fdc6209-78b3-4d88-8110-57936b671313 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3fdc6209-78b3-4d88-8110-57936b671313 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
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
chainloader	+1
```

Sorry for delayed post, I was away for a bit.

---

### Post by Arthur Archnix on 2007-08-12
Well, from what I've seen the error 17 message could be a number of things. 

If you've got two hard-drives though try setting the bios to auto-detect both.

It could be the UUID, plug in your external drive and check the UUID:
```
sudo vol_id /dev/sdb1
```
Make sure that matches what's in menu.lst

That's just what I gleaned from a quick glance around the forums. There's a great deal more though on this error, so have a good look around as your problem may already have a solution posted.

Regarding Windows Bootloader, if I understand you correctly this is a USB external harddrive with Ubuntu on it, but you've gone and installed the Grub to the hard-drive in the computer (sda1), correct?

Why not restore XP bootloader, then tell the bios to boot from USB hard-disk first, then install grub to sdb1 by inserting a live cd and following some of the instructions found all around on how to do that.

Anyway, looks like XP is a dell system, which sucks because they generally don't include a CD that lets you boot into recovery mode.  Anyway, this thread [here]("http://ubuntuforums.org/showthread.php?t=463534&highlight=Ted+Nancy") has a link to a tool that might work, but be sure to scroll down because the trick for XP is to not use the Vista switch.

---

