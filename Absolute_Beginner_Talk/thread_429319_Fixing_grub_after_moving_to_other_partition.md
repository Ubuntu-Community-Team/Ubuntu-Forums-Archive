---
title: "Fixing grub after moving to other partition"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by merike on 2007-05-01
Since that: [http://ubuntuforums.org/showthread.php?t=428252](http://ubuntuforums.org/showthread.php?t=428252) I've managed to get my Ubuntu installation on a partition I wanted. I also tried editing menu.lst and fstab, but something went wrong because I get grub error 22: No such partition.

Here's my menu.lst:
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
timeout		30

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
# kopt=root=UUID=a4763eca-ff5f-4458-bef5-334577473c03 ro
# kopt_2_6=root=/dev/hda3 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=5
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

And here my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
dev/hda3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
dev/hda4 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Ubuntu is on hda3 and swap on hda4. I feel so close getting all working again :roll:

---

### Post by indytim on 2007-05-01
did you tell grub where it's new home is?

At boot (while in grub), get to grub command:
grub> root(hd0)
grub>setup(hd0,2)

Exit and re-boot.  Hopefully things will be happy now.

Good Luck,

IndyTim

---

### Post by merike on 2007-05-01
> **indytim said:**
> At boot (while in grub), get to grub command:
grub> root(hd0)
grub>setup(hd0,2)
How do I do that? I can't type after error?

If I go from live cd's terminal to grub then "root (hd0)" gives "selected disk does not exist".

---

### Post by antoz on 2007-05-01
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

This link may be helpfull

---

### Post by merike on 2007-05-01
Last link didn't load for me.

However, the following worked:
grub> root (hd0,2)
grub>setup (hd0)

But I now have new problem. After that Grub loaded fine, but Ubuntu didn't.

I got "fsck died with exit status 16", then it says that I must perform manual check with root in read-only mode. After that it says it's in read-only mode and that "maintenance shell will now be started". I then get:
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: dircolors: command not found

Now what? New boot, no?

---

### Post by antoz on 2007-05-01
Here is the link again, it loads at my end, can't help you myself maybe someone with a bit more experience can help. Cheers A
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by merike on 2007-05-01
How foolish of me, I had:
```
# /dev/hda3
dev/hda3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
dev/hda4 none            swap    sw              0       0
```

but I should have had:
```
# /dev/hda3
**/**dev/hda3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
**/**dev/hda4 none            swap    sw              0       0
```

---

