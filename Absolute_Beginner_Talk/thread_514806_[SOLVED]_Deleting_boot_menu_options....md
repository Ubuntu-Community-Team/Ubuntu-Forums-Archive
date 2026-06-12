---
title: "[SOLVED] Deleting boot menu options..."
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by chatterjee on 2007-08-01
After updating a new option for bootting in Ubuntu has been added.I don't want to boot into the old kernel.What should I do to change the boot menu options?

Thanks in advance...

---

### Post by chatterjee on 2007-08-01
[quote="menu.lst"]# menu.lst - See: grub( 8 ), info grub, update-grub( 8 )
#            grub-install( 8 ), grub-floppy( 8 ),
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
#      password --*********************************
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
# kopt=root=UUID=f4b726d6-76cf-438f-9b6a-4afdc6b15c4f ro

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=f4b726d6-76cf-438f-9b6a-4afdc6b15c4f ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=f4b726d6-76cf-438f-9b6a-4afdc6b15c4f ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f4b726d6-76cf-438f-9b6a-4afdc6b15c4f ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f4b726d6-76cf-438f-9b6a-4afdc6b15c4f ro single
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
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
[/quote]

Where to change??And how?

---

### Post by KIAaze on 2007-08-01
```
gksudo gedit /boot/grub/menu.lst
```

And remove the entries you don't want.

P.S: There is also a GUI to edit menu.lst:
[http://ubuntuforums.org/showthread.php?t=228104]("http://ubuntuforums.org/showthread.php?t=228104")

---

### Post by KIAaze on 2007-08-01
Remove those two entries:
> title Ubuntu, kernel 2.6.20-15-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=f4b726d6-76cf-438f-9b6a-4afdc6b15c4f ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=f4b726d6-76cf-438f-9b6a-4afdc6b15c4f ro single
initrd /boot/initrd.img-2.6.20-15-generic

It is recommended to keep the recovery mode of the new kernel at least. ;)

---

### Post by doomster on 2007-08-01
you should edit /boot/grub/menu.lst using 
```
 sudo gedit /boot/grub/menu.lst 
```

in there you can edit what will be shown in grub menu. find something like 

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7072443d-4ee2-4e95-9053-7151700eead9 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7072443d-4ee2-4e95-9053-7151700eead9 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

[B]title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=7072443d-4ee2-4e95-9053-7151700eead9 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault[/B]

```
and put an "#" in frond of the old kernels boot option... i t will be something like 
```

[B]#title		Ubuntu, kernel 2.6.20-15-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.20-15-generic #root=UUID=7072443d-4ee2-4e95-9053-7151700eead9 ro quiet splash
#initrd		/boot/initrd.img-2.6.20-15-generic
#quiet
#savedefault[/B]

```

ps you should first of all keep a backup of the file, for any case..
to backup it use 
```
 sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup 
```

---

### Post by magoo on 2007-08-01
argh....

If those entries are there, usually the corresponding kernel package is also installed. Make sure to remove it instead of only removing the menu entry.

BEFORE you remove a kernel package (and the corresponding module package) make sure the new one works without any issue.

by the way, what is the problem of having those entries in your grub menu? By default it is the latest installed (or higher version number that is launched).

---

### Post by Obor on 2007-08-01
As said above, if you don't want the old kernels you might just as well remove them (they are about 80MB each) and they will disappear from the GRUB as well.

Search for linux-image in synaptic to find them. Make sure you don't remove the one you are using :)

---

### Post by chatterjee on 2007-08-01
Successfully edited the boot menu.Thank you all for you help...:D

BTW,would please mention how can I remove my older kernel,they don't show up in the Synaptic Packet Manager.

---

### Post by armandh on 2007-08-01
this dyslexic typist will leave well enough alone
at least until there is a GUI for this.
LUV Ubuntu over every other previous distro I have tried.
however a few machines will stay as XP
given things I use that wont work in vista either
Ubuntu just works and there is a possibility that if I wanted to learn 
I could do-up a driver for my DDS-32 printer
[current driver is a 2K beta]
but I think it would be easier to remote wake and remote desktop a basement machine left just for it.

---

### Post by MQMike on 2007-08-01
Rog131 tells you how to remove the kernels, if you wish:
[http://kubuntuforums.net/forums/index.php?topic=3082556.0](http://kubuntuforums.net/forums/index.php?topic=3082556.0)

Here’s my How-To on GRUB and editing menu.lst:
How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
(See the second post in this thread for menu.lst)

If you simply comment the unwanted kernels (using the hash marks #), then you have the option of keeping them or later removing them.

---

