---
title: "Grub bootloader help"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by linjiaoyang on 2006-04-17
Hi, 

I just installed ubuntu and ya, it's awesome. So, I formatted my pc, installed ubuntu, then installed windows XP home, then installed windows 2000. After, I installed grub from the ubuntu install cd.

So now, in the grub menu there's Ubuntu (+ recovery mode), and Windows 2000/XP/NT (loader).

What I want now is to add Windows XP and Windows 2000 to the boot menu to be loaded directly without going through the windows boot loader.

My Windows XP is on dev/hda4 and Windows 2000 on dev/hda3

This is my current menu.lst
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

#title		Ubuntu, kernel 2.6.12-9-386 
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
#initrd		/boot/initrd.img-2.6.12-9-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single
#initrd		/boot/initrd.img-2.6.12-9-386
#boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda3
title		Windows NT/2000/XP (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

```

Any help is greatly appreaciated

---

### Post by htinn on 2006-04-17
[QUOTE=linjiaoyang]My Windows XP is on dev/hda4 and Windows 2000 on dev/hda3[/QUOTE]

I suppose you could try modifying your menu.list to something like this:

```
...

title		Windows NT/2000/XP (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

title		Windows XP
root		(hd0,3)
savedefault
makeactive
chainloader	+1
```

I don't know whether that will work, but it might be worth a shot.

---

### Post by linjiaoyang on 2006-04-17
tried it, doesn't work. I don't remember the error message exactly, but it's the standard error i've seen most people get

---

### Post by Sutekh on 2006-04-17
Windows will not be happy that you put Ubuntu on the first partition.  You can fool it into thinking otherwise with the **map** commands.

Try
```
title		Windows NT/2000/XP (loader)
root		(hd0,2)
savedefault
map             (hd0,0) (hd0,2)
map             (hd0,2) (hd0,0)
chainloader	+1

title		Windows XP
root		(hd0,3)
savedefault
map             (hd0,0) (hd0,3)
map             (hd0,3) (hd0,0)
chainloader	+1
```

You can read the GRUB manual for more explanation

[GRUB manual - map](http://www.gnu.org/software/grub/manual/grub.html#map)

[GRUB manual - DOS/Windows](http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows)

---

### Post by not28 on 2006-04-17
How do I open menu.lst as a root user to edit the default value?

---

### Post by ds[de] on 2006-04-17
[QUOTE=not28]How do I open menu.lst as a root user to edit the default value?[/QUOTE]

Open a terminal, type 
```
sudo gedit /boot/grub/menu.lst
``` 
then you have the proper permission to edit the file.

Regards,
ds[de]

---

### Post by not28 on 2006-04-17
Thanks! (Actually I had discovered the sudo prior to reading this but thank you anyway.)

---

### Post by RAV TUX on 2006-04-17
I'm not sure how to do this, yet. Someone lastnight adviced burning a cd of Grub bootloader before loading Ubuntu....

:mrgreen:

---

