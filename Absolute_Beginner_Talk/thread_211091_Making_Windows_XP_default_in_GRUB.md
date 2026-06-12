---
title: "Making Windows XP default in GRUB"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by Skylander on 2006-07-07
Hi all,  I need a little bit of help configuring GRUB to boot up Windows XP by default when the timer finishes counting down.  How do I go about this?  Thank you for your help.

---

### Post by Rackerz on 2006-07-07
> **Skylander said:**
> Hi all,  I need a little bit of help configuring GRUB to boot up Windows XP by default when the timer finishes counting down.  How do I go about this?  Thank you for your help.

First you will need to open up your grub file:

```
sudo gedit /boot/grub/menu.lst
```

Then paste the file here.

---

### Post by Iarwain ben-adar on 2006-07-07
Hi,
First of all, welcome!

Now, i looked around a bit, and found that this MIGHT be a way to change it:
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
**default		0**

<snip>


## ## End Default Options ##
[B]
title		Ubuntu, kernel 2.6.15-25-386
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hdd7 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot[/B]

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hdd7 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdd7 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdd7 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd1,6)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

<snip>

```

So i guess you just change the "default 0" to "default x" where x=the number of your XP (start by 0, and count :D )

NOTE: BACK UP your /boot/grub/menu.lst ;)


Iarwain

---

### Post by Skylander on 2006-07-07
I got the Grub boot file for you guys.  Here goes:

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

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-25-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
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
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by someusernoob on 2006-07-07
Ok, open the file again if you allready closed it:

```

gksudo gedit /boot/grub/menu.lst

```

Then change default from 0 to 6. Only change the number.

So this:
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

```

should look like this:
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
default		6

```

SAVE THE FILE AND CLOSE IT

Why is it 6? Because at the end of the file, from this section:## ## End Default Options ##, Windows is the 6th option (the first option is 0, second option is 1 etc.)

```

## ## End Default Options ##

THIS ONE IS 0

title Ubuntu, kernel 2.6.15-25-386
root (hd1,0)
kernel /boot/vmlinuz-2.6.15-25-386 root=/dev/hdb1 ro quiet splash
initrd /boot/initrd.img-2.6.15-25-386
savedefault
boot

THIS ONE IS 1

title Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.15-25-386 root=/dev/hdb1 ro single
initrd /boot/initrd.img-2.6.15-25-386
boot

THIS ONE IS 2

title Ubuntu, kernel 2.6.15-23-386
root (hd1,0)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro quiet splash
initrd /boot/initrd.img-2.6.15-23-386
savedefault
boot

THIS ONE IS 3

title Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro single
initrd /boot/initrd.img-2.6.15-23-386
boot

THIS ONE IS 4

title Ubuntu, memtest86+
root (hd1,0)
kernel /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

THIS ONE IS 5

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

THIS ONE IS 6

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

```

Note that when something is added or removed from this list, you have to change the default again to which option Windows is then (and remember, start counting from 0)

---

### Post by Skylander on 2006-07-07
I'll be pleased to report that it works.  Thank you so much guys, you've saved me from getting brain damage from banging my head trying to find the right tutorial that's easy to follow.  The reason I needed windows to be default is that I have a TV Card and when I leave after setting it to record a show while I'm away,  I need it to go back into windows if there happens to be a reboot such as a storm caused one.  Thank you so much again!

---

### Post by Iarwain ben-adar on 2006-07-08
Glad to help you :D


Iarwain

---

### Post by kigina on 2006-07-08
I followed this and saved it, just change extension to htm

---

