---
title: "[SOLVED] Installation problem"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by chongchongworks on 2007-08-29
Hi, before i install Ubuntu into my computer, I have installed Freebsd, but after I installed Ubuntu with grub, it looks cannot recognise freebsd partition, i did not touch anything belongs to freebsd, so can someone tell me how i can fix that?

Thanks a lot.

---

### Post by jamvegan on 2007-08-29
Ubuntu reinstalled Grub, and apparently did not recognize FreeBSD in the process.  You will need to add an entry for FreeBSD to your /boot/grub/menu.lst file.  If you can mount your FreeBSD partition while running Ubuntu, you should be able to copy the entry directly from the one that was created when you installed FreeBSD.

---

### Post by chongchongworks on 2007-08-31
Hi, thank u for your reply,

Can u tell me what command I should add into grub, and other setup to boot from Freebsd?

Thanks, the following is my menu.lst:

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
# kopt=root=UUID=9b51e7d6-b83a-4dee-9ed2-272ade42c564 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,8)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

<cut > continuing in next post

---

### Post by chongchongworks on 2007-08-31
continue with last post
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
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9b51e7d6-b83a-4dee-9ed2-272ade42c564 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9b51e7d6-b83a-4dee-9ed2-272ade42c564 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9b51e7d6-b83a-4dee-9ed2-272ade42c564 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9b51e7d6-b83a-4dee-9ed2-272ade42c564 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,8)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by chongchongworks on 2007-08-31
continue with last post
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
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9b51e7d6-b83a-4dee-9ed2-272ade42c564 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9b51e7d6-b83a-4dee-9ed2-272ade42c564 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9b51e7d6-b83a-4dee-9ed2-272ade42c564 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9b51e7d6-b83a-4dee-9ed2-272ade42c564 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,8)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by jamvegan on 2007-08-31
From [FreeBSD documentation]("http://www.freebsd.org/doc/en_US.ISO8859-1/books/faq/disks.html#GRUB-LOADER"):

> title FreeBSD 6.1
    root (hd0,a)
    kernel /boot/loader
     

Where hd0,a points to your root partition on the first disk. If you need to specify which slice number should be used, use something like this (hd0,2,a). By default, if the slice number is omitted, GRUB searches the first slice which has 'a' partition.

(If you follow the link to read more, note that they refer to '/boot/grub/grub.conf', which is an alias for /boot/grub/menu.lst on some systems, such as Red Hat.)

---

### Post by chongchongworks on 2007-08-31
Thanks, that problem solved, and I found in the option menu of grub there are 2 "generic" and 2 "recovery", the only difference between them is the number, one is "15", the other is "16", 

Can I delete one of them in menu.lst? because it looks not neat.

---

### Post by splintercellguy on 2007-08-31
You can either comment them out or uninstall the 2.6.15 kernel.

---

### Post by jamvegan on 2007-08-31
If you've been running 16 with no problems, then you can certainly delete or comment out (with #) any section that you don't want to see in your boot menu.  It's probably a good idea to keep the recovery entry that is associated with the kernel version that you use, because it can be very helpful if you encounter problems in the future.

I like commenting rather than deleting, because then if you ever decide that you need/want one of the entries back (like memtest, which I always comment out), you can just un-comment it.

---

### Post by chongchongworks on 2007-09-01
Thanks a lot.

---

