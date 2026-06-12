---
title: "new grub entry?"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-05-28
every once in a while, when i do an update, it'll add a new entry to grub.  i use this new entry because it's apparently the newer version of ubuntu, but how can i get rid of the old ones?  and is that safe?  i just like having a nice, clean, compact grub screen.  :P  i'm a neat-freak.  thanks in advance!  (this will be my first time playing with grub, so please excuse my extremely basic questions.)

---

### Post by taurus on 2007-05-28
I assume you mean when you upgrade a kernel from synaptic/apt-get/aptitude.  You can go into synaptic and remove the old kernel that you don't need or use anymore and it should remove the entry in /boot/grub/menu.lst for you as well.

---

### Post by justifier on 2007-05-28
or theres the way i do it, not the "proper way" but, meh it works do

sudo nano /boot/grub/menu.lst 

and remove all of the old ones, its pretty obvious, there the ones at the end, aslong as you keep the new ones (one at the top of the list you can touch) you should be okay, oh, and you can change the title line too, if you so wish, 

the stuff you can delete will look like

title		Ubuntu
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=81fbe5da-bacb-43fd-81d3-362f9db5fab9 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-386
savedefault

just with a different title, and the kernal will be the old ones,

p.s. you can replace nano with what ever text editor you like to use:

---

### Post by locke.dragon on 2007-05-28
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
# kopt=root=UUID=9a9c1ae9-127c-45e5-b970-4fe44cd6380e ro

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
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9a9c1ae9-127c-45e5-b970-4fe44cd6380e ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9a9c1ae9-127c-45e5-b970-4fe44cd6380e ro single
initrd		/boot/initrd.img-2.6.20-16-generic
[b]
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9a9c1ae9-127c-45e5-b970-4fe44cd6380e ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9a9c1ae9-127c-45e5-b970-4fe44cd6380e ro single
initrd		/boot/initrd.img-2.6.20-15-generic[/b]

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

so i just delete the part in bold if i don't want those entries there, and then save right?

---

### Post by justifier on 2007-05-28
yup that simple

---

### Post by drs305 on 2007-05-28
No matter how you do it, make a backup copy first. 

There are a hundred ways to skin a cat. Another method to alter the grub menu is to comment out the old kernel (i.e. put # symbol in front of the lines that you don't want to see any longer. The advantage to this is that you can remove the # symbols should you need that kernel in the future (it will probably still be on the disk, you just won't see it in the grub menu if you have commented it out).

Yet another method is to change the line which contains " howmany=all " to another value, such as howmany=2 to limit the number of kernels visible. Notes: I believe that changing howmany will take affect only on the next kernel update, it won't change the number visible until that time. And you leave the comment symbol in place (don't know why).

---

