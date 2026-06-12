---
title: "Unable to boot to linux/use GRUB"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Callius on 2007-12-31
Hello.

First things first.  My system is set up with a 40 gb NTFS partition with WinXP, a 40 gb ext2 partition with Ubuntu 7.10, a 2 gb swap partition and the rest is a huge NTFS data store.

I had installed XP, then I installed Linux.  This allowed me to use GRUB to boot into either partition and it worked flawlessly.

I ran aground with my Linux install so I decided to reinstall Linux.... big mistake....

GRUB was coming up but would not load Linux and stated that NTLDR was corrupt.  I used a Linux live CD to modify my boot.ini to appear as follows:

```
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

Now, whenever I start my computer it automatically dumps me into the Windows Boot.  I've reinstalled Linux a number of times and GRUB refuses to take hold.

Basically, I can't boot into Linux.  Regardless of what I try.

Any suggestions on how to make windows boot take second fiddle to GRUB?

---

### Post by spiderbatdad on 2007-12-31
I'll admit IDK what you've done there...but could you post your /boot/grub/menu.lst?

---

### Post by dcstar on 2007-12-31
> **Callius said:**
> 
.........
Now, whenever I start my computer it automatically dumps me into the Windows Boot.  I've reinstalled Linux a number of times and GRUB refuses to take hold.

Basically, I can't boot into Linux.  Regardless of what I try.

Any suggestions on how to make windows boot take second fiddle to GRUB?

[http://ubuntuforums.org/showpost.php?p=117829&postcount=2](http://ubuntuforums.org/showpost.php?p=117829&postcount=2)

---

### Post by Callius on 2007-12-31
> **spiderbatdad said:**
> I'll admit IDK what you've done there...but could you post your /boot/grub/menu.lst?

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
# kopt=root=UUID=bc002cc7-a814-4cb5-a52f-efde6d928917 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bc002cc7-a814-4cb5-a52f-efde6d928917 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bc002cc7-a814-4cb5-a52f-efde6d928917 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

### Post by Callius on 2007-12-31
> **dcstar said:**
> [http://ubuntuforums.org/showpost.php?p=117829&postcount=2](http://ubuntuforums.org/showpost.php?p=117829&postcount=2)

Every time I type in "root (hd0, x)" it says "Error 21: Selected disk does not exist"

Does the fact that I have two HDDs matter?  One is SATA and one is IDE.  The SATA is set as primary and is where the linux and windows partitions are located.

---

### Post by Callius on 2007-12-31
It turns out that my SATA drive is HD1.  The only way I knew this was looking at my menu.lst and seeing it there.  Is there some other way (while using the live CD) to check?

What is the difference between HD1 and sdb1?  It seems to be two ways to say the same thing.

Also, I did the grub->root thing with HD1 (sudoing grub, I guess I missed that step), yet that didn't resolve the issue.  I still boot straight into windows.

---

### Post by logos34 on 2007-12-31
Go into the BIOS at startup and set the IDE to boot first.

---

### Post by Callius on 2007-12-31
Except my IDE is just an NTFS formatted data-dump with no boot sector.

Hrmm... is HD1 usually the IDE drive if there is a SATA one connected?

---

### Post by logos34 on 2007-12-31
> **Callius said:**
> Except my IDE is just an NTFS formatted data-dump with no boot sector.

Hrmm... is HD1 usually the IDE drive if there is a SATA one connected?

yes, but grub is (I think) on the mbr of the ide (the first 446 bytes of the first sector of the drive). i.e. it's bootable now, even if nothing on the bootsector of the NTFS data partition.

If you install ubuntu in a system with mixed sata and ide drives, grub and/or the ubiquity installer usually sees the ide channel first and puts grub on mbr of the ide drive (hd0), regardless of actual hard disk boot order or which drive the ubuntu root is on

---

### Post by Callius on 2007-12-31
Hrmm... interesting.

So, would the GRUB that's installed in the MBR on my IDE drive pull the menu.lst from the SATA drive?

---

### Post by logos34 on 2007-12-31
> **Callius said:**
> Hrmm... interesting.

So, would the GRUB that's installed in the MBR on my IDE drive pull the menu.lst from the SATA drive?

yep, that's why I suggested you change the boot order

---

### Post by Callius on 2008-01-01
This seems to have fixed it.

Thanks a lot.  It's really appreciated.

---

### Post by logos34 on 2008-01-01
> **Callius said:**
> This seems to have fixed it.

Thanks a lot.  It's really appreciated.

My pleasure!  

Enjoy Ubuntu and happy new year!

---

