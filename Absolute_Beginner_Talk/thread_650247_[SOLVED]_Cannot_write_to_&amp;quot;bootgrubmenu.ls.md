---
title: "[SOLVED] Cannot write to &amp;quot;boot/grub/menu.lst&amp;quot;"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by goblue on 2007-12-26
Hello, first time poster here.  I just installed Ubuntu Gutsy on a partition of my home machine, and cannot seem to change GRUB's "/boot/grub/menu.lst" file to edit my default OS back to WinXP (my wife uses this computer at home, and will get easily confused if XP doesn't boot automatically for her).

Anyhoo, back to the point.  I know what needs to be changed in the "/boot/grub/menu.lst" file to alter my preferences, but apparently I don't have "Permissions" to overwrite the file.  I'm logged in with Administrator privileges.  None of the native GRUB commands work ("update-grub", "grub", etc) because they can't seem to write to the file either.

One thing to note... the "/boot/grub/" directory has both a "menu.lst" and "menu.lst~" file in it, both of which cannot be overwritten or removed.  Is it possible something else is writing to this file?  I've rebooted a couple times, to no avail.  I don't know what would be using it so that I couldn't overwrite it.

Any help is appreciated, and sorry for the newbie question!

- Mike

---

### Post by LaRoza on 2007-12-26
```

gksudo gedit /boot/grub/menu.lst

```

Back it up with:

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bk

```

Run these in terminal, backup first.

---

### Post by forestpixie on 2007-12-26
to edit the file, backup first fro justin case
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.261207
```

```
gksudo gedit /boot/grub/menu.lst
```

once the file is open for editing you need to find the 'default' - it's a number near the top - I've posted mine below so you can see - that number needs to correspond to the entry for win

count the instances of title - to get the number, it starts from 0

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
default		[COLOR="red"]4[/COLOR]

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
# kopt=root=UUID=8f552ce7-3122-4440-92f1-543f1db6ad1c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

[COLOR="red"]title[/COLOR]		Ubuntu hardy (development branch), kernel 2.6.24-2-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-2-generic root=UUID=8f552ce7-3122-4440-92f1-543f1db6ad1c ro quiet splash
initrd		/boot/initrd.img-2.6.24-2-generic
quiet
[COLOR="red"]
title[/COLOR]		Ubuntu hardy (development branch), kernel 2.6.24-2-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-2-generic root=UUID=8f552ce7-3122-4440-92f1-543f1db6ad1c ro single
initrd		/boot/initrd.img-2.6.24-2-generic
[COLOR="red"]
title[/COLOR]		Ubuntu hardy (development branch), memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
[COLOR="red"]title	[/COLOR]	Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
[COLOR="red"]title[/COLOR]		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4f6494fc-353c-4d61-a5cf-33189c5fbb2a ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4f6494fc-353c-4d61-a5cf-33189c5fbb2a ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

---

### Post by goblue on 2007-12-26
Thanks, LaRoza.  That worked perfectly... It let me overwrite the file.  After looking the command up, it seems like a no-brainer now.  I'll just reboot real quick and see if it worked.  Thanks! :cool:

- Mike

---

### Post by LaRoza on 2007-12-26
> **goblue said:**
> Thanks, LaRoza.  That worked perfectly... It let me overwrite the file.  After looking the command up, it seems like a no-brainer now.  I'll just reboot real quick and see if it worked.  Thanks! :cool:

- Mike

No problem. Of course it worked, I usually don't give bad advice. :)

---

