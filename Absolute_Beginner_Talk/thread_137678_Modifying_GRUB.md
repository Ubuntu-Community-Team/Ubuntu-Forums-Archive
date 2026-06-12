---
title: "Modifying GRUB"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by Clark Nova on 2006-02-28
I'm about to reinstall Windows XP (spit) on a separate partition because my wife isn't a big fan of Ubuntu and plain refuses to use it. XP doesn't have a bootloader as such and will wipe my MBR when I do this so I need to know how to reinstall GRUB so I can select my Ubuntu partition again after I install Windows. Will I be able to do this using my Dapper Drake Live CD? Is there a guide somewhere?

Thanks:-D

---

### Post by nixclusive on 2006-02-28
You can use the install CD and enter 'expert' at the prompt. You'll be presented with a menu shortly, select 'install GRUB boot loader'.

I'm not sure whether this will include a chainloader image for WindowsXP. Wait a little more while more replies come in.

---

### Post by Clark Nova on 2006-02-28
Ok, having read another thread on a similar issue, here is the contents of my /etc/fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda2 /Windows ntfs nls=utf8,umask=0222 0 0

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy1  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy2  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy3  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy4  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy5  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy6  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy7  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy8  auto    rw,user,noauto  0       0
dev/hda2	/Windows        ntfs	nls=utf8,umask=0222        	0       0
```

and this is the what is in my /boot/grub/menu.lst file:

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
# kopt=root=/dev/hdb1 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-16-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-16-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-16-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-16-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-16-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-16-386
boot

title		Ubuntu, kernel 2.6.15-15-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-15-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-15-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-15-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-15-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-15-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

I'm going to be installing Windows into the same partition it is in on the menu.lst file as shown above (Windows isn't working currently but it still shows up in GRUB).

---

### Post by Ramses de Norre on 2006-02-28
Why do you have 9 lines in fstab for one device?

---

### Post by Clark Nova on 2006-02-28
[QUOTE=Ramses de Norre]Why do you have 9 lines in fstab for one device?[/QUOTE]


I have no idea, in fact I don't even have a floppy drive so I don't know why it is in there in the first place.:confused: 

I assume I can just delete all of those lines?

---

### Post by carverj on 2006-02-28
GDAY ppl :-D 
I am also about to install windies to partition 5 (hda5 below). Below is an example of my fstab. the last line of fstab is where I edited fstab to allow partition hda1 or hda5 to access my personal data in seperate home partition (hda6). hope this helps a little mate.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /media/hda5     ext3    defaults        0       2
/dev/hda6       /media/hda6     ext3    defaults        0       2
/dev/hda7       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hda6 /home ext3 defaults 0 2
```

I also have no working floppy, but somewhere along the line fd01 has been erased from fstab somehow. 

So I just go ahead and install windies in hda5 and then insert ubuntu breezy live, then type expert  to reactivate GRUB or is it press F2 or F3?
thanks for all z help
GO UBUNTU
___________________

"If we knew what it was we were doing, it would not be called research, would it?"
- Albert Einstein

---

