---
title: "Fedora dual boot problem"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by colemana on 2008-03-29
I've been using Ubuntu for a while now and I love it. However, I recently wanted to try out a few new OSes and I always wanted to test out Fedora. So I got the Live CD.

I have two hard drives so I decided to just leave the Ubuntu drive as it was and install Fedora on my extra drive. Everything went well and I made sure not to install a boot loader in Fedora. Then I went through some other posts and goodled some information and I did what they suggested and edit the menu.lst file.

but now I still can't get Fedora to boot, Grub goes straight into Ubuntu with no options. I'm going to post what menu.lst looks like incase maybe that's the problem. 

> title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=c681ed27-97e9-4372-b402-8f53a58d96ec ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=c681ed27-97e9-4372-b402-8f53a58d96ec ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu hardy (development branch), kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c681ed27-97e9-4372-b402-8f53a58d96ec ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c681ed27-97e9-4372-b402-8f53a58d96ec ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title 		Fedora (2.6.23.1-42.fc8)
root 		(hd1,0)
kernel 		/vmlinuz-2.6.23.1-42.fc8 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
initrd 		/initrd-2.6.23.1-42.fc8.img


Also, as you can tell I'm using the beta version of Hardy, so I hope that isn't a problem.

Thanks in advance for any help. Also... if this is the wrong forum I'm sorry, I just figured this was the place for it.

---

### Post by angry_johnnie on 2008-03-29
I think the entry for Fedora must go after the line that reads "End debian automagic kernels list."

It could be that.

---

### Post by colemana on 2008-03-29
> **angry_johnnie said:**
> I think the entry for Fedora must go after the line that reads "End debian automagic kernels list."

It could be that.

I tried that, sadly it didn't help anything. Thanks though.

---

### Post by PmDematagoda on 2008-03-29
Can you please post your full menu.lst?

---

### Post by colemana on 2008-03-29
> **PmDematagoda said:**
> Can you please post your full menu.lst?

No problem 


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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# kopt=root=UUID=c681ed27-97e9-4372-b402-8f53a58d96ec ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=c681ed27-97e9-4372-b402-8f53a58d96ec ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=c681ed27-97e9-4372-b402-8f53a58d96ec ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu hardy (development branch), kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c681ed27-97e9-4372-b402-8f53a58d96ec ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c681ed27-97e9-4372-b402-8f53a58d96ec ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


title 		Fedora (2.6.23.1-42.fc8)
root 		(hd1,0)
kernel 		/vmlinuz-2.6.23.1-42.fc8 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
initrd 		/initrd-2.6.23.1-42.fc8.img





```

---

### Post by colemana on 2008-03-29
Well... I'm feeling like an idiot.... 

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

could have something to do with a menu not showing up..... doh.

---

### Post by wolfen69 on 2008-03-29
did you change your boot order in BIOS?

---

### Post by pirast on 2008-03-29
install fedora's grub to the fedora partition, like /dev/sda5 and ubuntu's grub to your ubuntu partition like /dev/sda3 by running

grub-install /dev/sda5 from your fedora install and grub-install /dev/sda3 from your ubuntu install..


then install gag ([http://gag.sf.net](http://gag.sf.net)) to your mbr to select between the grub installs.

martin

---

### Post by flatwombat on 2008-03-29
As an alternative, you can try booting Fedora this way:

title Fedora
configfile (hdx,y)/grub/grub.conf  (where x,y refer to the hard drive and partition for Fedora).


Personally, when installing a new distro and keeping the old distro's grub, I install the new grub on the root partition (/dev/sda3 or whatever...check the 'advanced' bootloader options)  and then adding these lines to your /boot/grub/menu.lst:

title Fedora
root (hdx,y) ...again, substitute x,y for your drive and partition that refers to Fedora's install
rootnoverify (hdx,y)  ...yep, same here
chainloader +1

Be sure to go into Ubuntu's existing /etc/fstab and dump the UUID for the Fedora partition since it will have changed.  Substitute /dev/hda5 (or whatever) for UUID1293xxxxxxxxx/media/hda5.  If you don't do that ahead of time, Ubuntu will bork on the boot and you'll have to bypass the fstab error (ctrl D) to complete the Ubuntu boot.

---

