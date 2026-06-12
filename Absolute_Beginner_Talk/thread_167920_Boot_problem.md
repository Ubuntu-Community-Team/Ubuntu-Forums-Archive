---
title: "Boot problem"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by nelson2006 on 2006-04-29
[SIZE="2"]Hello everybody, ever since I installed the kubuntu desktop on my ubuntu I have problems on booting in. I can't select the operating system ](*,) . I have a dual boot system, now I can't iniciate en windows. Any clues to what happen here :-| ?[/SIZE]

---

### Post by Rinzwind on 2006-04-29
Yes.

Go into Ubuntu and get to a terminal session.
do

sudo gedit /boot/grub/menu.lst

If it is NOT there add Windows XP to the list.There are example on what to put there inside grub and on this forum
ALSO there's a feature telling grub to HIDE the menu.

> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		1

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu


Set timeout to 10
and a # before the hidemenu option

---

### Post by apjone on 2006-04-29
[QUOTE=nelson2006][SIZE="2"]Hello everybody, ever since I installed the kubuntu desktop on my ubuntu I have problems on booting in. I can't select the operating system ](*,) . I have a dual boot system, now I can't iniciate en windows. Any clues to what happen here :-| ?[/SIZE][/QUOTE]


Describe what happens when you try and boot, the screens and etc .

---

### Post by nelson2006 on 2006-04-29
[SIZE="2"]Ok, these are the messages I get:

** (gedit:5444): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.

The opens a blank window, I write Windows Xp and get the following message:

Could not save the file /boot/grub/conf/menu.lst.
Unexpected error: File not found

What can I do?????
[/SIZE]

---

### Post by nelson2006 on 2006-04-29
[SIZE="2"]When I boot I get the usual grub screen But can not select anything with the up/down buttons.[/SIZE]

---

### Post by apjone on 2006-04-29
[QUOTE=nelson2006][SIZE="2"]Ok, these are the messages I get:

** (gedit:5444): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.

The opens a blank window, I write Windows Xp and get the following message:

Could not save the file /boot/grub/conf/menu.lst.
Unexpected error: File not found

What can I do?????
[/SIZE][/QUOTE]


in a terminal type

sudo vi /boot/grub/menulist

then put windows XP in there and save and quit

---

### Post by Rinzwind on 2006-04-29
Nelson.

It's 

sudo gedit /boot/grub/menu.lst

I made a typo in the directory.

---

### Post by nelson2006 on 2006-04-29
[SIZE="2"]Ok, guys this is what I get when I do the sudo gedit:


# Splashimage line added by kubuntu-grub-splashimages package
splashimage=(hd0,2)/boot/grub/splashimages/KUBUNTU_splashscreen_blue_neon_logo_03.xpm.gz

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
timeout		20

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
# kopt=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu, kernel 2.6.15-21-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-21-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-21-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-21-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-21-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-21-386
boot

title		Ubuntu, kernel 2.6.15-20-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-20-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-20-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-20-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-20-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-20-386
boot

title		Ubuntu, kernel 2.6.15-19-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-19-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-19-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-19-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-19-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-19-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

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





Everything looks normal to me.[/SIZE]

---

### Post by Rinzwind on 2006-04-29
Yes looks perfect to me too. Weird.

Does the menu appear when you boot up?
Or does it say to hit ESC for a few seconds?

---

### Post by nelson2006 on 2006-04-29
[SIZE="2"]The grub menu appears as normal but nothing in the menu is shadowed so that I can select with the up/down buttons to log in with windows xp. I'm updating the system to see what happens. Very weird :-k .[/SIZE]

---

### Post by infoseeker on 2006-04-29
I had that problem too (but not really a problem) :rolleyes: 
All I did was change (in menu.lst)
> splashimage=(hd0,3)/boot/grub/splashimages/KUBUNTU_splashscreen_blue_neon_logo_03.xpm.gz
to
> splashimage=(hd0,3)/boot/grub/splashimages/KUBUNTU_splashscreen_faded_sky.xpm.gz
as the first splash produces a black background as well as a black cursor.  Difficult to see the position of the cursor.

---

