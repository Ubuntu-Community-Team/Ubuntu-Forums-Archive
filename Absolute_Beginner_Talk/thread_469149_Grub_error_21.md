---
title: "Grub error 21"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by delta3 on 2007-06-09
Well, I installed Ubuntu on an external hard drive but when I try to boot up, it gives me grub error 21(I'm a newb so I don't know what the problem is). Thing is, even if I disconnect the external, when I try to boot using my internal with windows XP it still gives grub error 21. I can only use my computer using the live cd. All help appreciated.

---

### Post by GrueTamer on 2007-06-09
Could you post your /boot/grub/menu.lst file?

---

### Post by Princey on 2007-06-09
Is your computer set to boot from external devices?

---

### Post by delta3 on 2007-06-09
> **GrueTamer said:**
> Could you post your /boot/grub/menu.lst file?

Here ya go

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
# kopt=root=UUID=80ca22bf-ae02-4243-becc-e31836947fb5 ro

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=80ca22bf-ae02-4243-becc-e31836947fb5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=80ca22bf-ae02-4243-becc-e31836947fb5 ro single
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
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by delta3 on 2007-06-09
Also, is there anything I can try to get back in to windows?

---

### Post by logos34 on 2007-06-09
> **delta3 said:**
> Also, is there anything I can try to get back in to windows?

Grub is installed on the Master boot record of the internal drive.  With the usb drive plugged in and on, set the bios to boot from the internal disk first.  Does that get you the grub menu?

---

### Post by delta3 on 2007-06-09
> **logos34 said:**
> Grub is installed on the Master boot record of the internal drive.  With the usb drive plugged in and on, set the bios to boot from the internal disk first.  Does that get you the grub menu?

No, that didn't work

---

### Post by delta3 on 2007-06-09
I hate to double post but I really need some help. Thanks in advance

---

### Post by pistcivet on 2007-06-09
As a last resort, you should be able to restore the MBR
and boot Windows using one of these methods:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Basically, you boot from an XP cd, select "recovery console", and run fixmbr. :)

---

### Post by logos34 on 2007-06-09
sorry for the delay.

I thought maybe it went to the internal mbr.  Maybe it did but there's some other problem.

In any case, do what pistcivet suggested above and restore the windows bootloader to the internal mbr.  Then you'll have edit your menu.lst, changing all instances of '(hd1,0)' to '(hd0,0)'--i.e. 'groot' line + the ubuntu section--and WinXP from '(hd0,0)' to '(hd1,0)'.  You see, during install grub detects and labels the internal drive as the first drive, (hd0); but the minute you change the boot order putting the external drive first, it becomes (hd0).  Don't forget to edit /boot/grub/device.map to reflect this change.  Then restore grub to the mbr of the external disk and set the bios to boot from it.

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

---

### Post by delta3 on 2007-06-09
Sorry for not posting earlier, I had to leave for a bit. All I have is a Windows XP recovery CD and Unless I'm going blind, I don't see an option to get to the recovery console.

---

### Post by logos34 on 2007-06-09
I'm only familiar with the install cds, where on the first screen you have a choice of install or recovery console and then your press 'R'...Are you sure there's nothing about 'fixmbr' or 'fixboot'?

---

### Post by delta3 on 2007-06-09
When I use the recovery cd as a boot cd it readies it's files and then takes me to a partitioning screen asking where I want to install windows. No other options are presented.

---

### Post by logos34 on 2007-06-09
If you have access to another computer you could download [Supergrub]("http://supergrub.forjamari.linex.org/") and burn it to a cd and see if that works.

---

