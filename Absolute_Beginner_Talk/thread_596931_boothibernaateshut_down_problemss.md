---
title: "boot/hibernaate/shut down problemss"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by ubunt22rock on 2007-10-30
i got 3 problems..i have gutsy gibbon installed on my laptop

1->when i boot up after i select my os (ubuntu)to boot it goes blank and goes directly to my log in screen....i have seen an ubuntu logo and a load status bar in my friend's system

2->when i hibernate it does not hibernate it goes to locked mode and when i unlock it, there is a balloon sayin my computer failed to sleep

3->when i shut down it does to a blank screen and my ssystem does not poweroff automatically..i do it manually al the time


pls help me out

---

### Post by arkara on 2007-10-30
do you boot with acpi=off?

---

### Post by ubunt22rock on 2007-10-30
how do i check that

---

### Post by ubunt22rock on 2007-10-30
can anybody please help me with tese problems

---

### Post by arkara on 2007-10-30
give this one 

```
sudo gedit /boot/grub/menu.lst
```

and then push ctrl+f and type on the frame acpi=off and see if this finds you anything if it does then you are booting with acpi=off and it is very normal for this to happen

---

### Post by ubunt22rock on 2007-10-30
dude the file doesn't have anything specified as acpi at all

here's the file

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
# kopt=root=UUID=635a09b5-dd42-4570-bc93-acc3b3604158 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,8)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=635a09b5-dd42-4570-bc93-acc3b3604158 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=635a09b5-dd42-4570-bc93-acc3b3604158 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,8)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Acer Windows Backup
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by arkara on 2007-10-31
my friend all seems to be fine with all your setting here
this behavior that you report are not normal and you know it.
see this section:

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=635a09b5-dd42-4570-bc93-acc3b3604158 ro ***_quiet splash_***
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=635a09b5-dd42-4570-bc93-acc3b3604158 ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,
kernel /boot/memtest86+.bin
quiet

now replace this highlighted thing with splash.(only remove the word quiet)
this will show you the processes that happen when ubuntu boots up.
if you see anything saying failed. report it here.
but in general i recomend that you back up files that you need and then reinstall ubuntu.
oh and something else. sorry that i can't reply faster to your posts

---

### Post by ubunt22rock on 2007-10-31
oh thats fine as long as ur helpin out im thankful...i'l try it out

---

### Post by arkara on 2007-10-31
tried that yet?
i don't really think that this will help you though but give it a shot.it might reveal something

---

### Post by ubunt22rock on 2007-11-01
hey thanks
d boot details do appear..
but d hibernate problems still remain..and my machine doesnot power off by itself either

---

### Post by ubunt22rock on 2007-11-07
hello

---

