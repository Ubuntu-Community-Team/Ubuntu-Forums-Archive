---
title: "Help w/ Duel boot- boots xp but not Ubuntu"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by jimmybute on 2007-08-19
Hello all,

Need help with duel boot:

2 hard drives - connect to Promise/Maxtor Ultra 133 TX2 ATA controller.

Ubuntu on Master drive
Win XP on slave

from the Grub boot loader I have the option to boot both OS's, XP boots perfect, Ubuntu hangs up 
screen says: Starting up... with blinking cursor 

I've tried an Ubuntu install by itself ( unplugged the xp drive, just used 1 drive ) reinstalled it and it booted with no problems. Also tried jumper on Ubuntu dive at cable select and master positions.

Please help,

---

### Post by benerivo on 2007-08-19
Not sure I can be of much help as your setup should work, and not much happens for you to work with or understand the problem. Post the contents of your /boot/grub/menu.lst file to see if there is anything that might need changing, although by the sound of it the bootloader begins to load the kernel - so i don't think that will be to blame.

Also, i think a workaround may be to have separate installations on each drive (where Ubuntu works for you), and just use the BIOS as a bootloader by changing the drive orders in the boot sequence.

---

### Post by djsroknrol on 2007-08-19
Have you tried booting in Verbose mode?...It might give you a clue as to where it's hanging up...possibly a boot option is in order...

---

### Post by jimmybute on 2007-08-19
Hey THANKS for the reply,

from fdisk:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   150239879    75119908+  83  Linux
/dev/sda2       150239880   156296384     3028252+   5  Extended
/dev/sda5       150239943   156296384     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders, total 156355584 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   156328514    78164226    7  HPFS/NTFS
```

from menu.lst:
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
# kopt=root=UUID=16d7bcc4-6bbb-4366-acf3-a994a2bbac10 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=16d7bcc4-6bbb-4366-acf3-a994a2bbac10 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=16d7bcc4-6bbb-4366-acf3-a994a2bbac10 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

I'm a long time Windows user and a BIG NOOBIE to Linux.

How do I boot in "verbose mode"?

---

### Post by benerivo on 2007-08-22
To get verbose mode, I think you have to take out the word 'quiet' from the grub menu entry in this file...

/boot/grub/menu.lst


The entry you are looking for will probably look something lie this...

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5fg48gf-55fgdfgf54-5454fg-54fgf ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

---

### Post by Arthur Archnix on 2007-08-22
Sounds like Grub may be installed to the wrong drive. Also post the output of 
```
gksudo gedit /etc/fstab
```

---

