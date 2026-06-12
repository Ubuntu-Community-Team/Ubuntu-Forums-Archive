---
title: "Small problems for a beginer"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by sn0m on 2007-01-08
Hi
here is another beginner with annoying questions.
Question 1. How can I change GRUB, i have dual boot with ubuntu and win xp. I was just wandering how can i change it to start straight to ubuntu, without producing the load up ladder, and to pres escape if i need to get in the menu to load memory test or xp.
below is my menu list.

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
timeout		2

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
# kopt=root=UUID=51894118-a070-4ccc-abe4-590193a6ddde ro
# kopt_2_6=root=/dev/hda2 ro

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

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

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

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

--------------------------------------------------------------------------
Question 2  I experimented with KDE dekstop-enviroment a while ago and didn't like it. I removed it but now, i am left with a i a kubuntu loading up blue screen, this is immediately after i hit enter at grub menu to load ubuntu then after the system loads it comes back to ubuntu. Is there a way to reverse that to ubuntu. Interesting, if I choose ubuntu generic from menu it looks ok.
Question 3, i made the mistake of assigning 50gig of my hardware to xp when i first installed ubuntu. Since I have not used XP for a month now and I am downloading most of the staff in UBUNTU, i am kinda running out of space. I did do a research here, and a few threads said that it could be a problem trying to resize win partitions. Does anybody know any easy way, considering my extreme beginingess.
Question 4, last one, hurrah. I have a compaq pressario V5000 and whenever i write, cursor seem to jump with no notice wherever it likes, any idea how to fix it.
Thanks
Koli

---

### Post by rich.bradshaw on 2007-01-08
Easiest way with menu is to change timeout to 0, then to get the menu you have to press down just as grub is loading. This way you can change to XP and other options, but usually it will go straight to Ubuntu without you noticing the menu.

---

### Post by rich.bradshaw on 2007-01-08
Oh, try running

sudo apt-get clean

and

sudo apt-get autoclean

to get a bit more space on your drive.

---

### Post by usien on 2007-01-08
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

remove # from the last line:

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu


simple?

---

### Post by usien on 2007-01-08
do u want to completely remove the xp partition or resize it?anyways u shud try watever u want wid the ubuntu/kubuntu (gparted/qtparted) live cd but remember to backup ur important data.

---

