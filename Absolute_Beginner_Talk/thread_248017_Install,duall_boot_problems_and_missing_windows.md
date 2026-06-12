---
title: "Install,duall boot problems and missing windows"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by badboybrody on 2006-08-31
Okay, first off if I'm in the wrong spot I apoligize. This is uncharted waters for me. My problem is this. I went to install Ubuntu last as a duel boot, with windows xp media wich has been a royal pain. I did an automatic partion of 23GB. Which took, I found later when I thought I had to do a manual partion and there it was. As far as I know windows is still on my computer. I can access F2 at boot up but that is all. Do I still have windows and how do I verify? Can I fix this mess and do still do a dual boot? Or,how can I unistall ubuntu and start over.. Thanks for your help in advance. Brody

---

### Post by benfindlay on 2006-08-31
WHen turn your pc on, try repeatedly hitting the ESC key; this should show you the GRUB boot loader which will allow you to pick from the operating systems installed. If windows isn't listed it doesn't mean it's gone however, you just need to add it into GRUB's config file again!

Hope this helps

---

### Post by tatimmer on 2006-08-31
The Ubuntu install cd has the capability to delete existing partitions converting them to free space, then it can partition the free space as ext and install itself.  I have adual boot with Win98 and on boot-up grub gives me a choice of selecting Ubuntu or Win98 to boot. My hard drive is 10G, 4G for Win98 and 6G for Ubuntu.

On boot up do you get a screen with choices for which OS to boot ?  If the answer is no, you may find the live cd useful with programs such as fdisk, parted or qtparted for examining the state of your hard drive.

---

### Post by badboybrody on 2006-08-31
Thanks for the suggestion ben, how do I add windows to the grub config file file? As far as I know it was never there. If I use the disk they sent me I can access ubuntu, otherwise i get the grub interface, But I don't know how to use it. Thats why I was wondering if a clean install might be better.  Grub reminds me of Dos back in the early'90's, And that was scary enough. lol. Thanks for your help
 tatimmer, thanks I will take a further look at my hard drive and see if I can figure anything out. I appreciate the help.

---

### Post by benfindlay on 2006-08-31
with the grub interface I take it windows isn't listed as the last option? If its there, then you just navigate with the arrow keys and select it by pressing Enter.

If it isn't then you need to add it by booting into ubuntu (not your live cd, but the installed OS) and logging in, Then click on Applications>>Accessories>>Terminal

This puts you in the terminal, which is your command line interface.

Once here, type:```
cp /boot/grub/menu.lst /boot/grub/menu.lst.bak/CODE]
This creates a backup of the file you want to edit (cp = copy, /boot/grub/menu.lst = source file and /boot/grub/menu.lst.bak = destination backup file)

Then type
[CODE]sudo gedit /boot/grub/menu.lst
```
This open the file for editing using gedit (ubuntu equivalent of notepad)

In here you should see something like the following:
[HTML]
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

title		Ubuntu, kernel 2.6.15-26-686
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-686 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-26-686
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

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title Microsoft Windows XP
rootnoverify (hd2,0)
savedefault
makeactive
chainloader +1
[/HTML]

The last bit here> title Microsoft Windows XP
rootnoverify (hd2,0)
savedefault
makeactive
chainloader +1

should be added if it isn't already present and that should solve your problem! Please note that the section > rootnoverify (hd2,0) may be different depending on your hardware

_NB_:Please please please make a backup of your menu.lst file. If this goes wrong you've effectively destroyed your computer's boot record!

---

