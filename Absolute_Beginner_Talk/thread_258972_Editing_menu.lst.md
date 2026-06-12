---
title: "Editing menu.lst"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by foxknob on 2006-09-16
I have Ubuntu installed on my main HD and just installed Dreamlinux on the second one. How do I edit the menu.lst to allow me to choose between the two?  Here is my current menu.lst:

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
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=/dev/sda1 ro

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

title		Ubuntu, kernel 2.6.15-26-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-686 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-26-686
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by whizbaby on 2006-09-16
```

title Other-Linux-Thingy
root (hd0,0)
kernel /boot/*name_of_the_kernel* root=*/dev/sdb1* ro quiet splash
initrd /boot/*initrd_name*
savedefault
boot

```
replace *name_of_the_kernel*, */dev/sdb1* and *initrd_name* by the one's fitting your system and put in the menu.list **above** the *debian automagic kernellist*.
(all information should be in the /boot directory of the Dreamlinux partition  )

---

### Post by jordanmthomas on 2006-09-16
Also, you will need to change root(hd0,0) to match your dreamlinux installation

---

### Post by whizbaby on 2006-09-16
Already late. Grumble.:oops:

---

### Post by foxknob on 2006-09-16
Still having trouble.:confused: 
Getting errors about having trouble parsing numbers (Error 23) and unrecognizable strings.
Dreamlinux is installed on a 20 gig HD that's recognized as hdb1
It's swap drive is hdb2

Ubuntu is installed on sda1  (Dont know why it's refered to with an "S" instead of an "H")

Here's what's installed in the /boot folder of hdb1:
[B]Config-2.6.14-kanotix-9  (a plain text file)
initrd  (unknkown type 84.7kb)
System.map-2.6.14-kanotix-9  (a plain text file)
vmlinuz  (2.2 mb link to unknown)
vmlinuz-2.6.14-kanotix-9 (2.2 mb unknown)
[/B]

When I installed Dreamlinux on hdb1 I took the option to NOT install GRUB since it was already installed with Ubuntu on sda1.
I have hdb1 mounted and can access it from sda1.
I'd just like to have Dreamlinux as one of my options when booting.

---

### Post by bodhi.zazen on 2006-09-16
title Dream Linux
root (hd1,0)
kernel /boot/vmlinuz-2.6.14-kanotix-9 root=/dev/hdb1 ro quiet splash
initrd /boot/initrd
boot

---

### Post by foxknob on 2006-09-16
With that I'm now getting this error:

root (hd1,0)
Error 21: Selected disk does not exist

When I run 'mount' from the command line, I'm getting this:

[B]/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-686/volatile type tmpfs (rw)
/dev/hdb1 on /media/littledrive type ext3 (rw)[/B]

This is the contents of the device map /boot/grub/device.map.
(fd0)   /dev/fd0
(hd0)   /dev/hdb
(hd1)   /dev/sda

---

### Post by JayTee on 2006-09-17
If the boot section for Dreamlinux looks like this:
title Dream Linux
root (hd1,0)
kernel /boot/vmlinuz-2.6.14-kanotix-9 root=/dev/hdb1 ro quiet splash
initrd /boot/initrd
boot

Change it to look like this and try it.
title Dream Linux
root (hd0,0)
kernel /boot/vmlinuz-2.6.14-kanotix-9 root=/dev/hdb1 ro quiet splash
initrd /boot/initrd
boot

---

### Post by foxknob on 2006-09-17
Jay Tee, tried your suggestion and get "file not found"

At this point, I'm open to any suggestions including starting from scratch with the DreamLinux drive.  I do , however have the Ubuntu drive set up and is running beautifully, so I'd hate to loose the work I've put in on that one.

---

### Post by jordanmthomas on 2006-09-17
Will dreamlinux install grub?  If so, you could jot down your current kernels in your menu.lst and add them to the one dreamlinux makes.

---

### Post by bodhi.zazen on 2006-09-17
This may be a problem with your BIOS. Is there an update?

---

