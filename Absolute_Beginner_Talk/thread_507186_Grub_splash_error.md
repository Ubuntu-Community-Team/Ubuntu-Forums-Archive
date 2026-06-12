---
title: "Grub splash error"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by cawill on 2007-07-22
I am trying to add a splash image to grub, but I keep gettings:
'Failed to load splash Image'

Line in menu.lst is: 'splashimage=(hd0,0)/boot/grub/grubuntu.xpm.gz'
And grubuntu.xpm.gz is in the /boot/grub/ folder.

I have also tried (hd0,1) and (hd1,0) and various others. My /boot partition is on the 1st hard disk and the 1st partition, how do I get this working and is the 'hd' part even right?

Thanks in advance, Chris.

---

### Post by Tux Aubrey on 2007-07-22
try it without the disk partition reference at all:

```
splashimage=/boot/grub/grubuntu.xpm.gz
```

---

### Post by bradleyd on 2007-07-22
ok where did you get your splash image did you make it or was it a download. Also what does the bottom of your menu.lst look like.

---

### Post by cawill on 2007-07-22
I downloaded the grubuntu splash from gnome-look.

Menu.lst:
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
splashimage=(hd0,0)/boot/grub/grubuntu.xpm.gz
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
# kopt=root=UUID=83169e70-d0ba-4168-9455-6bd03a30e993 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=83169e70-d0ba-4168-9455-6bd03a30e993 ro quiet splash
initrd		/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=83169e70-d0ba-4168-9455-6bd03a30e993 ro single
initrd		/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=83169e70-d0ba-4168-9455-6bd03a30e993 ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=83169e70-d0ba-4168-9455-6bd03a30e993 ro single
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

```

In /etc/fstab/ all my drives are mounted as sd instead of hd, is that normal and does that make a difference with grub?

---

### Post by bradleyd on 2007-07-22
ok root(0,0) is correct, so I would think maybe the splash image is bad. You could try to find an image 640x480.
Then type from command line:```
convert -resize 640x480 -colors 14 splash.png splash.xpm && gzip splash.xpm
``` 
Then:
 ```
chmod 644 spalsh.xpm.gz
```
copy splash.xpm.gz to /boot/grub. Then use your splashimage=(hd0,0)/boot/grub/splash.xpm.gz

p.s. All newer kernels label all drives sda, sdb,sdc, etc... this is fine.

---

