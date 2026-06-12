---
title: "How to default into XP?"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by JacobRogers on 2007-05-10
Hey I'm sending my computer away to get the screen fixed, it's a laptop, and for the sake of ease I want it to just boot straight into windows xp.  How can I edit grub to do this?

I'd really like to just set it up where it just skips grub or only stays on grub for like a second, and then goes automatically into XP, and then when I get the laptop back I'll fix it back so that it will mainly go into Ubuntu.


Thanks, you guys are fantastic.

---

### Post by Najand on 2007-05-10
Can you send us your /boot/grub/menu.lst file?

---

### Post by annda on 2007-05-10
this should tell you all you need to know and do:
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

if not, ask some more here.

---

### Post by JacobRogers on 2007-05-10
It's very confusing because I have multiple listings in my menu.lst and I don't know exactly what I should count.  Here's my menu.lst

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=2a19e045-086f-40c6-8743-f50d5b27773c ro

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
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2a19e045-086f-40c6-8743-f50d5b27773c ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2a19e045-086f-40c6-8743-f50d5b27773c ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=2a19e045-086f-40c6-8743-f50d5b27773c ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=2a19e045-086f-40c6-8743-f50d5b27773c ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=2a19e045-086f-40c6-8743-f50d5b27773c ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=2a19e045-086f-40c6-8743-f50d5b27773c ro single
initrd		/boot/initrd.img-2.6.17-10-generic

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
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

What should I change, also I want to, temporarily, make it so that it only stays on the bootload for like one second, and I can't find any help on that.

---

### Post by Milt888 on 2007-05-10
Or you could just download GrubEd and it will do anything you want with your boot options.
Great little prog. Just do a forum search.

---

### Post by JacobRogers on 2007-05-10
gahhh ignore the smilies

---

### Post by annda on 2007-05-10
> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

timeout needs to be 1

if i counted right, win is the 7th entry, and since computers start counting from 0, it is number 6 - you need to change the number in this section:

> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

to

> default 6

---

### Post by JacobRogers on 2007-05-10
Hey I used GrubEd, and after I figured out how to install it it did everything I wanted.  Thanks guys you're the best community ever.

---

### Post by kpraytor on 2007-05-12
Ok, I could really use some help to be able to get back into windows. Here's what my menu.lst file looks like:

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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=e77dffe4-2297-425a-a5da-1caf98e37be1 ro

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
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e77dffe4-2297-425a-a5da-1caf98e37be1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e77dffe4-2297-425a-a5da-1caf98e37be1 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Compared to the last guys file, mine looks like I don't have a Windows OS on here at all! I know that whenever I put Ubuntu on here, I made sure to leave the Windows partition completely alone. Any help would be greatly appreciated!!

---

### Post by confused57 on 2007-05-12
From a terminal, see what the output of this is:
```
sudo fdisk -l
```
the -l is a small "L"
this will show your partition table

If Windows is on your 1st partition, your entry would look something like this:
```
title Windows XP
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1
```

If Windows is on the 2nd partition, root would be (hd0,1).

Added:  On 2nd thought, since Ubuntu is on (hd0,0)...your Window's partition may have been overwritten...see what the "fdisk -l" output shows.

---

### Post by kpraytor on 2007-05-12
Ok, here's the ouput when I punch in "sudo fdisk -l":

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks       Id  System
/dev/sda1   *           1            365     2931831   83  Linux
/dev/sda2            4792        9730   39665664   7  HPFS/NTFS
/dev/sda3            4427        4791   2931862+  5  Extended
/dev/sda5            4427        4791   2931831   82  Linux swap / Solaris

Partition table entries are not in disk order


I think it's there, but I'm not really not sure! Anymore help is greatly appreciated as always!

---

### Post by annda on 2007-05-12
the only windows partition you have is sda2, which is the secend partition:

/dev/sda2 4792 9730 39665664 7 HPFS/**NTFS**

so use the section from previous post with (hd0,1). be sure to write it at the bottom of the file, after this line:
### END DEBIAN AUTOMAGIC KERNELS LIST

if you put it before, it will be overwritten when you update the kernel.

---

