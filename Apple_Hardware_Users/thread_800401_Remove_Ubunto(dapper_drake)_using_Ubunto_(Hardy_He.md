---
title: "Remove Ubunto(dapper drake) using Ubunto (Hardy Heron)"
date: 2008-05-19
forum: Apple Hardware Users
---

### Post by Mac_Wii on 2008-05-19
First time post as i'm a first time Ubuntu user, also a first time Mac Book user aswell.

The situation is like this.

I got a MacBook of a mate with no Mac OSX on it. It only had Ubunto Dapper Drake. He said he didnt want it because it just wasn't cutting it. He wanted a Mac OSX back on, So i've tried to get one back on but no joy really. I've tried Panther and Leopard. I've tried TransMac and Macdrive to create mac discs but no joy there either. I've also tried Apple Disk utilities for windows to create a Mac disk.

So i've dumped the Mac OSX idea and decided to upgrade to Hardy Heron ( a move which i'm glad i made.

My problem is now that i managed to down HARDY burn a live cd and install it on the mac i notice DAPPER is still there. I thought it would be a complete install and basically install right over DAPPER.

When i boot the mac up i get the usual 30 second boot screen letting me decide what to use ie. HARDY or Dapper?!

So my question is how do i delete the dapper insatll from the macs hard drive??

is there a tutorial for this?

Will i need to basically wipe the slate clean and re-install HARDY? if so how do i do this??


Thanks to any replies in advance. I'm sure somone will be able to help me.


P.S I notice my spelling mistake in the titles.....sorry.....can they be changed??

---

### Post by gsiliceo on 2008-05-19
Can you post the outcome of this two commands please?
> sudo fdisk -l
> cat /boot/grub/menu.lst

---

### Post by Mac_Wii on 2008-05-19
Like i mentioned before mate. I'm totally new to Mac. Ho do i enter a command line?

Do i do this from ubuntu or do i do it at boot?

---

### Post by cyberdork33 on 2008-05-19
> **Mac_Wii said:**
> Like i mentioned before mate. I'm totally new to Mac. Ho do i enter a command line?

Do i do this from ubuntu or do i do it at boot?
start a terminal, (look in the application menu).

type in or copy/paste the commands.

---

### Post by Mac_Wii on 2008-05-19
Thanks mate.

I'll post first thing in the morning. I'm in the uk and its gone 2am. I never expected such a quick response.

---

### Post by Mac_Wii on 2008-05-27
> **gsiliceo said:**
> Can you post the outcome of this two commands please?

this is the result of the first command:

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000048bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         479     3847536   83  Linux
/dev/sda2             480        7296    54757552+   5  Extended
/dev/sda5            7120        7296     1421721   82  Linux swap / Solaris
/dev/sda6             480        6944    51930049+  83  Linux
/dev/sda7            6945        7119     1405656   82  Linux swap / Solaris

Partition table entries are not in disk order
bleu@bleu-laptop:~$ 


and the second

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
# kopt=root=UUID=4ed4c5dc-3d2a-4afb-96da-a0f302b43514 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4ed4c5dc-3d2a-4afb-96da-a0f302b43514 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4ed4c5dc-3d2a-4afb-96da-a0f302b43514 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4ed4c5dc-3d2a-4afb-96da-a0f302b43514 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4ed4c5dc-3d2a-4afb-96da-a0f302b43514 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, kernel 2.6.17-10-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, kernel 2.6.17-10-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot



Does this help you at all?

---

### Post by Mac_Wii on 2008-05-27
Please someone help me. The old Ubuntu is taking up much needed space.

Is there a simple way to delete it?

What if i do a new install stright from the live cd? Will this erase all previous existance of the othere Ubuntu installs?

---

### Post by cyberdork33 on 2008-05-27
> **Mac_Wii said:**
> Please someone help me. The old Ubuntu is taking up much needed space.

Is there a simple way to delete it?

What if i do a new install stright from the live cd? Will this erase all previous existance of the othere Ubuntu installs?
you need to install again, and make sure you choose to use the entire disk when prompted. This will delete all the partitions currently on the disk.

---

### Post by Mac_Wii on 2008-05-27
> **cyberdork33 said:**
> you need to install again, and make sure you choose to use the entire disk when prompted. This will delete all the partitions currently on the disk.

cheers mate.

I was afraid of this. I've just today got it all in ship shape order.

Looks like its time for a re-install then....:lolflag:

At least i've still got my Live cd.

Next thing after this is getting wireless sorted:confused:

---

### Post by cyberdork33 on 2008-05-27
> **Mac_Wii said:**
> cheers mate.

I was afraid of this. I've just today got it all in ship shape order.

Looks like its time for a re-install then....:lolflag:

At least i've still got my Live cd.

Next thing after this is getting wireless sorted:confused:well you don't have to, I thought that is what you were asking about... 

you can use gparted to delete partitions that you don't want and resize the remaining partitions to take up the space.

---

### Post by Mac_Wii on 2008-05-27
> **cyberdork33 said:**
> well you don't have to, I thought that is what you were asking about... 

you can use gparted to delete partitions that you don't want and resize the remaining partitions to take up the space.


As i'm totally knew to all this i'm probarly better off going down the whole install route. This way i know its all in and done as per the live cd.

Could you link me to the correct version that i should be using to install it.

EDIT: Found the link.

---

### Post by cyberdork33 on 2008-05-27
> **Mac_Wii said:**
> As i'm totally knew to all this i'm probarly better off going down the whole install route. This way i know its all in and done as per the live cd.

Could you link me to the correct version that i should be using to install it.

EDIT: Found the link.
Live CD is fine.

---

### Post by Mac_Wii on 2008-05-27
> **cyberdork33 said:**
> Live CD is fine.

I'm currently downloading this to my pocket hdd at work. Its different to the one i installed on my mac.

[http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)

I originally used the one straight from the ubuntu download page.  Is there any major difference?

It seemed to install and run fine?!

---

### Post by cyberdork33 on 2008-05-28
> **Mac_Wii said:**
> I'm currently downloading this to my pocket hdd at work. Its different to the one i installed on my mac.

[http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)

I originally used the one straight from the ubuntu download page.  Is there any major difference?

It seemed to install and run fine?!
Yes it is for powerpc cpus not Intel cpus. So if you have a Macbook, that is not the one you want.

---

### Post by Mac_Wii on 2008-05-28
> **cyberdork33 said:**
> Yes it is for powerpc cpus not Intel cpus. So if you have a Macbook, that is not the one you want.


I downloaded the the power pc one from the link i mentioned earlier and it doesnt work. Burned to a cd and then tried to install on the macbook, no joy.

Funny thing is the ubuntu hardy heron i have installed is the wrong one and its working great with no hic-ips. it updates every day no problem.

Can you see any problem in me just leaving it as is and running the current one?

I'll just have to deal with the other install taking up room on my hdd.

---

### Post by cyberdork33 on 2008-05-28
> **Mac_Wii said:**
> Can you see any problem in me just leaving it as is and running the current one?

I'll just have to deal with the other install taking up room on my hdd.
no, but it is not ideal...

---

### Post by Mac_Wii on 2008-05-28
> **cyberdork33 said:**
> no, but it is not ideal...

when i tried the ppc install i tried the nomal install and the altrenate install.
Whith the first nothing happened, but when i used the alternate install cd it started updating the current hardy os. The an error popped up saying something about not bein a "debian disc!"

---

### Post by cyberdork33 on 2008-05-28
> **Mac_Wii said:**
> when i tried the ppc install i tried the nomal install and the altrenate install.
Whith the first nothing happened, but when i used the alternate install cd it started updating the current hardy os. The an error popped up saying something about not bein a "debian disc!"you are not supposed to be using the PPC disc. You use the normal Install disc from the Ubuntu homepage.

---

