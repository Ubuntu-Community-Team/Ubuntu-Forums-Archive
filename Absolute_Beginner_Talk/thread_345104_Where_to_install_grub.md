---
title: "Where to install grub?"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by grim_d on 2007-01-23
Hi all, i'm a new linux user (installed first time yesterday) and ive been running the grub boot loader off a floppy because i wasnt entierly sure what to do with it.

This was fine while i was messing around getting used to ubuntu, but now i want to start using more permanantly so i was looking for a more permanant solution than always booting the grub from a floppy.

So before i get to my problem here the way i have things set up

HDA - Windows XP drive, 80gb
HDB - CD/DVD drive
HDC - Ubuntu drive, 120gb
HDD - 160gb Storage drive

now i did a fresh install of ubuntu onto HDC, same as last time (well i used text mode instead of OEM this time) and when it got to the GRUB screen i told it to install the MBR to HDC, my ubuntu drive, all went well and i though things were good.

Alas when i tried to boot it from grub i get error 17, damn, luckily i still had the floppy so i can still boot into ubuntu from it but i really want something more permanent and im not sure what to do.

So any help would be most appreciated, especially if i don't have to install ubuntu again :lol:

Thanks.

---

### Post by mikewhatever on 2007-01-23
Can you please post you GRUB menu.
sudo gedit /boot/grub/menu.lst

---

### Post by grim_d on 2007-01-23
> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=/dev/hdc1 ro

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

title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdd1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1


there you go, i wasnt sure exactly what bit you wanted

---

### Post by mikewhatever on 2007-01-23
Since you're saying Ubuntu is on HDC, it should be root (hd2,0)
title Ubuntu, kernel 2.6.15-26-386
root (hd1,0)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hdc1 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-386
savedefault
boot

I'd say your Ubuntu section should look like this
title Ubuntu, kernel 2.6.15-26-386
root (hd2,0)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hdc1 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-386
savedefault
boot

title Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root (hd2,0)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hdc1 ro single
initrd /boot/initrd.img-2.6.15-26-386
boot

title Ubuntu, memtest86+
root (hd2,0)
kernel /boot/memtest86+.bin
boot

---

### Post by grim_d on 2007-01-23
ok i changed the hd1's to hd2's and now i get error 17 regardless of trying to boot from hard drive or floppy.

I'm going to do a fresh install, where should i install GRUB to? I dont want it on my XP drive because i'm planning on doing a fresh XP install soon.

Cheers

---

### Post by grim_d on 2007-01-23
i'm going to be cheeky and bump this because of how quickly it dropped off the page, man these are some busy forums :lol:

---

### Post by mikewhatever on 2007-01-23
Sorry it didn't work. It looks like for the configuration you want, you still should install GRUB to the MBR of Ubuntu HD. Hopefully, someone more knowledgeable will help you to sort out the order. Keep that floppy at hand though.

---

### Post by pay on 2007-01-23
> **mikewhatever said:**
> Since you're saying Ubuntu is on HDC, it should be root (hd2,0)I think that is wrong. I'm pretty sure that it doesn't count non harddrive IDE devices. And since HDC is the 2nd harddrive, counting from 0, it would be (hd1,X)

---

### Post by grim_d on 2007-01-23
> **mikewhatever said:**
> Sorry it didn't work. It looks like for the configuration you want, you still should install GRUB to the MBR of Ubuntu HD. Hopefully, someone more knowledgeable will help you to sort out the order. Keep that floppy at hand though.

well i get error 17 when i try booting off the floppy now too, must have messed something up. No worries :)

I tried installing it to the ubuntu drive first, that didnt work, should i install it to a different partition on it or what? I'm going to do a fresh install.

> **pay said:**
> I think that is wrong. I'm pretty sure that it doesn't count non harddrive IDE devices. And since HDC is the 2nd harddrive, counting from 0, it would be (hd1,X)

it was set up as (hd1,0) insitially, or do you literally mean it should be (hd1,X)

---

### Post by logos34 on 2007-01-23
> I think that is wrong. I'm pretty sure that it doesn't count non harddrive IDE devices. And since HDC is the 2nd harddrive, counting from 0, it would be (hd1,X)

I agree.  One way to find out for sure: check /boot/grub/device.map

---

### Post by grim_d on 2007-01-23
> **logos34 said:**
> I agree.  One way to find out for sure: check /boot/grub/device.map

cant get into ubuntu anymore to check :(

---

### Post by pay on 2007-01-23
Well I mean that X is a variable depending on what partition Ubuntu is installed on, and since I don't know your partition layout I couldn't tell you for sure that it was on partition 0. I didn't want to mislead you by putting a partition number there.

---

### Post by grim_d on 2007-01-23
> **pay said:**
> Well I mean that X is a variable depending on what partition Ubuntu is installed on, and since I don't know your partition layout I couldn't tell you for sure that it was on partition 0. I didn't want to mislead you by putting a partition number there.

ok i though so, i only had the 2 partitions, the first one and the swap..as far as i'm aware. I just want to do a fresh install now :(

---

### Post by pay on 2007-01-23
To get back in, fire up a liveCD and then open up a terminal.```
sudo su
mkdir /mnt/ubuntu
mount /dev/hdc3 /mnt/ubuntu #again, whatever your partition is
```And then you can change it with```
sudo nano /mnt/ubuntu/boot/grub/device.map
```

---

### Post by grim_d on 2007-01-23
ok will do.

looks like i cant acctually do what i want to do with the grub.

if i were to swap my linux drive to the primary would i be able to put the grub on it then and have it work? because according to what ive read the grub will not work at all if placed on the 2nd drive.

---

