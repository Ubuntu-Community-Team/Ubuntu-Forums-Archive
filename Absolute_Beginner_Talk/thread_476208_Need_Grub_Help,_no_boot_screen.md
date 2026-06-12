---
title: "Need Grub Help, no boot screen"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by durrell on 2007-06-17
I installed Fedora, took it back off and now Ubuntu refuses to boot. I don't even see a Grub screen..all I see is the grub command prompt:

grub>

What in the world do I do? I'm posting this from my Linux System Rescue CD. I've tried reinstalling grub via the Live CD like this:

```

sudo grub

root (hd0,4)

setup (hd0,4)

```

What do I do? Please help..right now I can't boot into anything and I really don't want to lose my entire install because I know it's fixable.

Thanks!

---

### Post by Gwasanaethau on 2007-06-17
Hi there,

After going into 'sudo grub', you can try the command:
```
find /boot/grub/stage1
```
This will list the partitions where grub is already installed. Can you please post what comes up after you enter this? Thanks.

The rest of it looks good - you probably just need to make sure the numbers match whatever is already on your hard-drive.

---

### Post by durrell on 2007-06-17
Yeah, when I type that in it shows (hd0,4)..should have mentioned that's where I got the (hd0,4) from. That's why I'm stumped as to why it won't show my bootloader.

---

### Post by Gwasanaethau on 2007-06-17
Ahh, I see…hmm…that one's tricky. Unfortunately I'm all out of ideas, sorry. I only know that procedure because I had to do it myself once.

---

### Post by alienexplorers on 2007-06-17
Put in your instal cd and enter terminal.  Then enter grub and then at the grub menu type:
> find /boot/grub/stage1)
you will get an output such as (hd#,#)
type
> root (hd#,#)
type
> setup (hd#)
the last line should only include the hard drive number not the partition number.

---

### Post by durrell on 2007-06-17
My menu.lst file:


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
# kopt=root=UUID=e59350b2-779b-4d43-a79f-4ef180f25107 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e59350b2-779b-4d43-a79f-4ef180f25107 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e59350b2-779b-4d43-a79f-4ef180f25107 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e59350b2-779b-4d43-a79f-4ef180f25107 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e59350b2-779b-4d43-a79f-4ef180f25107 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


Edit:

When I type "find /boot/grub/stage1" I get a  "No such file or directory" error, but when I click on the Disk from the Live CD I can see /boot/grub/..



# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

---

### Post by durrell on 2007-06-17
When I type "find /boot/grub/stage1" I get a  "No such file or directory" error, but when I click on the Disk from the Live CD I can see /boot/grub/..

Edit: Did you mean you want me to do "sudo grub" before I do the find?

---

### Post by Gwasanaethau on 2007-06-17
> **alienexplorers said:**
> …the last line should only include the hard drive number not the partition number…

Aha! I knew it would be something simple like that!

---

### Post by durrell on 2007-06-17
> **Gwasanaethau said:**
> Aha! I knew it would be something simple like that!

That's EXACTLY what it was. I'm posting this from my Ubuntu install.

Thank you a TON alien, and you too gwasanaethau. :D

---

### Post by Gwasanaethau on 2007-06-17
> **durrell said:**
> That's EXACTLY what it was. I'm posting this from my Ubuntu install.

Thank you a TON alien, and you too gwasanaethau. :D

:lol: You're welcome, but I wasn't really much help there! Glad to hear you got it sorted, though.

---

