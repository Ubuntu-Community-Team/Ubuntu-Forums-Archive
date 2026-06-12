---
title: "Ubuntu / Windows XP (Default OS)"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by c-breakdown on 2007-04-03
I wanted to set up an ubuntu partition on my mother's computer, however I don't want it to be the default OS on her pc.  Is it possible to set up ubuntu and keep Windows as the computer's default OS?

---

### Post by hyper_ch on 2007-04-03
yes, after installation of ubuntu it will be the default OS but that can then be changed in the grub config :)

---

### Post by nsleiman on 2007-04-03
sure man, if you install GRUB (guess its a must) you will have the option to choose betweeen different installed OS's on the PC (maybe you need to change the order to make it start after several seconds with Windows)

---

### Post by Wally68 on 2007-04-03
Yeah, you can set the default to be any entry in /boot/grub/menu.lst. This file is actually documented pretty well. There'll be a line "default 0" meaning grub will boot the first entry by default. change that to whichever entry points grub to windows. That is, if windows is the third entry in menu.lst, then set the default to 2. Be aware that each time you install a new kernel, it will be entered at the top of the list, thus moving the older entries down, meaning you'll have to edit the /boot/grub/menu.lst for each kernel update.
Tom

I was reading my own /boot/grub/menu.lst and found the following:
```
 ## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false
```
I've never seen it before, let alone tried it, but it should allow kernel updates without having to re-edit menu.lst each time if set to true

---

### Post by mikewhatever on 2007-04-03
You can choose Windows to be booted by default by editing grub menu.lst
Here is the example of mine with Windows booting by default, grub menu hidden, and the timer set to 5 secs.
> gksudo gedit /boot/grub/menu.lst

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
[COLOR="Blue"]default		6[/COLOR]

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[COLOR="Blue"]timeout		5[/COLOR]

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Blue"]hiddenmenu[/COLOR]

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
# kopt=root=UUID=4f9dc7fd-2e2f-4892-b608-c393bc60dd9a ro
# kopt_2_6=root=/dev/sda7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda7 ro quiet
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda7 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda7 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda7 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
#title		Windows Recovery Partition
#root		(hd0,1)
#savedefault
#makeactive
#chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
#title		QuickPlay
#root		(hd0,2)
#savedefault
#makeactive
#chainloader	+1



as opposed to the default
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
[COLOR="Blue"]default		0[/COLOR]

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Blue"]#hiddenmenu[/COLOR]

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
# kopt=root=UUID=4f9dc7fd-2e2f-4892-b608-c393bc60dd9a ro
# kopt_2_6=root=/dev/sda7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda7 ro quiet
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda7 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda7 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda7 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
#title		Windows Recovery Partition
#root		(hd0,1)
#savedefault
#makeactive
#chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
#title		QuickPlay
#root		(hd0,2)
#savedefault
#makeactive
#chainloader	+1


---

### Post by Zuph on 2007-04-03
You can also try out the Ubuntu installer if you don't like the idea of messing with GRUB config files:

[http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html](http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html)

---

