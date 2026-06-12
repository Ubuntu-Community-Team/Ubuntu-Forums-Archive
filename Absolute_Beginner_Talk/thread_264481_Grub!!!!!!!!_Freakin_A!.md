---
title: "Grub!!!!!!!! Freakin A!"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by ironslave on 2006-09-24
ok i need to move around some stuff... i have converegd over to ubuntu and deleted windows... the 34GB of space i turned into an EXT3 partition now has all of my ubuntu files copied from the original install (so i now have 2 copys of ubuntu) i have ubuntu on HDA2 i need to get grub to load to HDA3 instead and make my old ubuntu copy a backup drive... how would i go about editing grub's setup to do this? !?!?!?!?!

---

### Post by bodhi.zazen on 2006-09-24
How did you move your files? and why not use hdb3 as your back up???? :confused:

At any rate, to answer your question, just edit /boot/grum/menu.lst.

```
sudo grub
```

At the grub prompt type:
```
root (hd0,2)
setup hd0
```

---

### Post by ironslave on 2006-09-24
> **bodhi.zazen said:**
> How did you move your files? and why not use hdb3 as your back up???? :confused:

At any rate, to answer your question, just edit /boot/grum/menu.lst.

```
sudo grub
```

At the grub prompt type:
```
root (hd0,2)
setup hd0
```


```
setup hd0
``` produces error 11 unrecognzed device string
and the reason being is hda2 is 10GB and its parition is after the hda3 and hda3 is 34GB i would like the space

---

### Post by bodhi.zazen on 2006-09-24
Oooops :redface:

Try setup (hd0)

Note that is a zero not a capital o.

---

### Post by ironslave on 2006-09-24
ummm.... it didnt work.... im still booting from my old drive
i used live CD to copy my files over with nautilus  i manually mounted my partitions to my live CD desktop and sudoed nautilus to have full drive access

---

### Post by bodhi.zazen on 2006-09-24
I'm not sure if your copy method is kosher.

At any rate, edit /boot/grub/menu.lst

Change root (hd0,1) to root (hd0,2).

---

### Post by ironslave on 2006-09-24
ok so i have no clue which ROOT to edit theres quite a few, would you mind showing me?

also could the 2 copys of grub be a problem?

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
default		X_sequence

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
# kopt=root=/dev/hda2 ro

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

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by bodhi.zazen on 2006-09-24
LOL :lol:

```
sudo gedit /boot/grub/menu.lst
```

Edit these two:> title Ubuntu, kernel 2.6.15-27-386
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd /boot/initrd.img-2.6.15-27-386
savedefault
boot

title Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single
initrd /boot/initrd.img-2.6.15-27-386
boot

Like this```
title Ubuntu, kernel 2.6.15-27-386
[b]root (hd0,2)
kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro quiet splash[/b]
initrd /boot/initrd.img-2.6.15-27-386
savedefault
boot

title Ubuntu, kernel 2.6.15-27-386 (recovery mode)
[b]root (hd0,2)
kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro single[/b]
initrd /boot/initrd.img-2.6.15-27-386
boot
```

---

### Post by ironslave on 2006-09-24
ok that worked... but now my networking card is inop (new drive)... im back on the other drive with my old kernal..... any ideas... maybe away to reinstall my drivers?

---

### Post by bodhi.zazen on 2006-09-24
Error message?

ifup eth0?

---

### Post by ironslave on 2006-09-24
it says device allready configured.....

another thing is that the networking program wont run on my user profile but will run in root..... eth0 was deactivated on my root pc... i tried to activate it and it took forever. when it activated it did nothing

---

