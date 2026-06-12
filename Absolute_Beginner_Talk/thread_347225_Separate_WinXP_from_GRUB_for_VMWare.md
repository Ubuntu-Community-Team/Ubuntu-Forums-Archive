---
title: "Separate WinXP from GRUB for VMWare?"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by pastaq on 2007-01-26
Hi, relatively new to Ubuntu and Linux. just started in sept. I'm not yet ready to totally trash windows yet so i set up VMWare Worksation to use instead of a lengthy dual-boot  crapfest.

The problem is when I try to boot my win XP partition i get a grub 21 error. I was wondering if there was a way to set it so GRUB ignores my Win XP. I'm pretty sure (but not positive) GRUB is installed on sda with my windows while Ubuntu is on sdb. I cant figure out how to install GRUB on sdb only  so i can set it as primary boot in BIOS and then restore my MBR for the windows XP partition. Is that even the best way to do it?

I'm using 2 250gb SATA2 Western Digital HDD I've also already mounted the NTFS using ntfs-3g and the updated fuse for 2.6.1.

heres my sudo fdisk -l

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29644   238115398+  83  Linux
/dev/sdb2           29645       30401     6080602+   5  Extended
/dev/sdb5           29645       30401     6080571   82  Linux swap / Solaris

Disk /dev/sdc: 2048 MB, 2048729600 bytes
64 heads, 63 sectors/track, 992 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         992     1999749+   6  FAT16

```

EDIT: oh yeah, using 6.10 Edgy

---

### Post by Cheiron on 2007-01-27
If I understand you correctly, you have Grub installed to sda, with options to boot windows from that drive or ubuntu from the other. Grub errors out onyl when you try to boot windows?

could you post the contents of your /boot/grub/menu.lst file?

---

### Post by pastaq on 2007-01-28
grub errors out when i try to run VMware to boot, i don't get to the OS Selection screen.

Here it is.
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
timeout		120

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
## hiddenmenu

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
# kopt=root=UUID=94a0f81c-1603-43b0-b197-81fbfe1f29bb ro
# kopt_2_6=root=/dev/sdb1 ro

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

title		Boot to: Ubuntu, 6.10 Edgy Eft
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Boot to: Ubuntu, 6.10 Edgy Eft(recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Boot to: Memory Test
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Boot to: Windows XP SP2
root		(hd0,0)
makeactive
chainloader	+1
```

---

### Post by Cheiron on 2007-01-28
Nothing really looks off in your menu.lst file as far as I can see.

If you are trying to boot off of your windows partition under linux, Grub *might* be erroring out if it cannot read/detect sdb as well or because the drive order/labeling is somehow off inside VMWare, assuming that you are trying to mount real partitions in VMWare but are only bothering to mount sda. I dount that is the case, though. The case may be that grub itself doesn't like being run under the VM.

Definately one way would be to use the BIOS boot selector, and put the XP MBR back on sda. (It's actually what I do after having my own fight with GRUB about an IDE connector card) Possibly WinXP's bootloader will handle better under the VM. 

Watch out, though. Its been my experience that pre-installed copies of windows XP don't like being run in VMs because it changes the underlying hardware. XP has a kind of a melt-down. One solution would be to create a virtual disk and put another copy of XP on that.

I don't know if you've already dismissed this, but let me suggest, if you're just looking to run common windows applications, that you take a look the Wine proect; [http://www.winehq.com]("http://www.winehq.com") Its a compatability layer that allows you to run some windows applications in linux sort of natively. I've got IE6 running, as well as some 3D games and Photoshop 7. It's actually fairly decent at most things, including 3D/gaming. it actually does better than VMWare at that, since VMWare (IIRC) simulates a pretty pathetic graphics card. EDIT: also take a look at [http://frankscorner.org/]("http://frankscorner.org/") for help with installing specific applications under wine

Sorry I can't help you fix the problem directly, but hopefully someone else can.

---

