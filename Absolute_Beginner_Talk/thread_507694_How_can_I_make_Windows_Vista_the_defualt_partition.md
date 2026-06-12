---
title: "How can I make Windows Vista the defualt partition to be booted?"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by superprogrammer on 2007-07-23
As the title suggests, I'm searching for a method that will force vista to load after the timout instead of my Ubuntu partition, consequently making it the default partition.  Could anyone help me out on this?

Below I will post the menu.lst from /boot/grub/ so you can help me better.

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
# kopt=root=UUID=833eefae-2a6e-4533-bd2d-5d55cb97429d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=833eefae-2a6e-4533-bd2d-5d55cb97429d ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=833eefae-2a6e-4533-bd2d-5d55cb97429d ro single
initrd		/boot/initrd.img-2.6.20-16-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by asmoore82 on 2007-07-23
I would comment out the "Other operating systems label AND move the windows to the static boot stanza's section directly before the automagic list... your new menu.lst follows with the changes bolded:

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
[b]
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
[/b]
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
# kopt=root=UUID=833eefae-2a6e-4533-bd2d-5d55cb97429d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=833eefae-2a6e-4533-bd2d-5d55cb97429d ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=833eefae-2a6e-4533-bd2d-5d55cb97429d ro single
initrd		/boot/initrd.img-2.6.20-16-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

[b]# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root[/b]

```

---

### Post by Bosambo on 2007-07-23
BACKUP BEFORE YOU FIDDLE WITH GRUB!

Right at the top there's and entry called "default num" with the default set to 0...change that to 1...

Not sure but that MIGHT set Ubuntu Recovery mode to the default in which case try again and this time enter 2.

A more dangerous way would be to cut the Ubuntu entries and paste them below the "Other operating systems:" line and paste the Windows entry in it's place...but I wouldn't

---

### Post by sailor2001 on 2007-07-23
default num 0 is set for ubuntu generic.  Watch when you boot up and count down from the ubuntu generic (0) to your xp... which may be 3-5 etc...just change the default 0 to that number in sudo gedit /boot/grub/menu.lst

---

### Post by asmoore82 on 2007-07-23
changing the default num is the wrong thing to do in this situation...

as long as windows is at the bottom or your boot list you can never be sure which 'num' it will be.
Future Ubuntu updates will add more Ubuntu entries and leave the old ones behind for rescue situations.
Ergo your windows will be pushed further and further down the list unless you place it before the automagic kernel list as i suggested.

Making a backup copy of menu.lst before editing it is a very good idea though.

---

### Post by fumduck on 2007-07-23
[http://ubuntuforums.org/showthread.php?t=394967&highlight=grub+boot+order]("http://ubuntuforums.org/showthread.php?t=394967&highlight=grub+boot+order")

that look shoiuld explain all but basically

# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0                   

you wqant to change that 0  to what looks like 3 on your menu lst... and that should boot windows..
because  I think this  counts as one..

 This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

Ok ?? hope that helps.. Peace.

---

### Post by mcduck on 2007-07-23
> **asmoore82 said:**
> changing the default num is the wrong thing to do in this situation...

as long as windows is at the bottom or your boot list you can never be sure which 'num' it will be.
Future Ubuntu updates will add more Ubuntu entries and leave the old ones behind for rescue situations.
Ergo your windows will be pushed further and further down the list unless you place it before the automagic kernel list as i suggested.

Making a backup copy of menu.lst before editing it is a very good idea though.
Actually changing the default number is the right thing. That's why it's there. But you also need to change "updatedefaultentry" to true so the default entry number gets updated when kernel update adds new kernel entries to GRUB.

```
## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true
```

In this case the default number should be 3, as both recovery mode and the divider are counted as entries.

---

### Post by superprogrammer on 2007-07-23
Thanks for all the replies, I followed mcduck's advice.  It auto-booted into Vista no problem, I just needed this becuase I am not the only one to use this computer in my family,  and my little sisters love to play their games.  So, thanks to everyone.

---

### Post by MQMike on 2007-07-23
asmoore82’s method is the simplest (and perhaps most understandable)-- Windows is then always in position zero and it will never change, so setting default = 0  does the trick now and forever; no need to change options.
But glad you got it working.

---

