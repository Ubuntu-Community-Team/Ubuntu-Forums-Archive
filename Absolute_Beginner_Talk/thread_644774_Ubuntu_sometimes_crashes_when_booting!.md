---
title: "Ubuntu sometimes crashes when booting!"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-12-19
Well, I used Ubuntu 64 bit and it worked perfectly. Now, I use Ubuntu 32 bit due to compatibility issues, and use GNU GRUB to select what to boot between the two. If I now boot to Ubuntu 64 bit it works fine, but if I boot to Ubuntu 32 bit, it shows me the loading screen, and then crashes. After generally 5 or 6 boots I can do it work correctly. Does anyone have an idea of whats the problem?

I let you with my menu.lst file:

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
default		1

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=faaed0b8-37e3-4b4a-b86e-d38b3eb64c61 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

splashimage=(hd0,1)/boot/grub/splash.xpm.gz

## ## End Default Options ##

title		Sistemas operativos
root

title		Ubuntu 7.10 32-bit
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=faaed0b8-37e3-4b4a-b86e-d38b3eb64c61 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot

#title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=faaed0b8-37e3-4b4a-b86e-d38b3eb64c61 ro single
#initrd		/boot/initrd.img-2.6.22-14-generic

#title		Ubuntu 7.10, memtest86+
#root		(hd0,1)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10 64-bit
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=11f622da-749f-4596-9e43-8f9216d7a0cc ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

### Post by Fixman on 2007-12-19
help! this is important!

---

### Post by Joeb454 on 2007-12-19
It looks like your entry for the 32 bit system is pointing to the same place grub thinks it's installed.

I'm not entirely sure, but that could be worth looking into

---

### Post by spiderbatdad on 2007-12-19
what do you mean when you say crashes? Does it just hang at a black screen? Have you tried doing nothing for 5-6 minutes to see if the splash screen eventually comes up?

---

### Post by Fixman on 2007-12-19
> **spiderbatdad said:**
> what do you mean when you say crashes? Does it just hang at a black screen? Have you tried doing nothing for 5-6 minutes to see if the splash screen eventually comes up?

I mean that USplash comes, and when finishes the screen turns black, but all tty's are working, so this is probably an X error. Anyway, if I try to restart GDM from some tty, it goes to the same black screen. If I kill X by ctrl+alt+backspace, then it turns to a "write-only" console (like tty8 ).

Oh, and by the way, if I reset many (like 5 or 6) times the computer, it magically seems to work perfectly.

---

### Post by spiderbatdad on 2007-12-19
sounds like a graphics card drivers problem

---

### Post by Fixman on 2007-12-20
> **spiderbatdad said:**
> sounds like a graphics card drivers problem

I doubt it, since my 64-bit Ubuntu works perfectly

---

