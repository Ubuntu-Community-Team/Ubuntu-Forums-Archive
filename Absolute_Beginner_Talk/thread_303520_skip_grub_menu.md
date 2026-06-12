---
title: "skip grub menu?"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by Ansible on 2006-11-20
Every time I boot my XUBUNTU machine, I have to hit ESC at the grub menu and then hit enter to start the boot process.  Is there a way to configure it so it will boot into the default after a few seconds?  I keep booting my machine and expecting to come back 10 minutes later and find it booted up, but instead its stuck on the grub menu again.

---

### Post by Bachstelze on 2006-11-20
That's the way it should behave by default... Pleas paste the contents of /boot/grub/menu.lst

---

### Post by Jimmy_r on 2006-11-20
That sounds strange.
Could you post your /boot/grub/menu.lst here?

---

### Post by Ansible on 2006-11-20
Here's the file:

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
# kopt=root=/dev/hda1 ro

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
# defoptions=quiet

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


---

### Post by Bachstelze on 2006-11-20
With that config, it definitely *should* boot Ubuntu after 3 secs... Could you sescribe more precisely what you see at boot-time ?

---

### Post by Ansible on 2006-11-20
Here's what it looks like:

> GRUB Loading stage1.5


GRUB loading, please wait...
Press 'ESC' to enter the menu... 2   _


Where the final '_' is the blinking underscore cursor.

---

### Post by niki001 on 2006-11-20
try editing your /boot/grub/menu.lst with the following options:

    First make a backup :
       sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
    Second edit your menu :
       sudo gedit /boot/grub/menu.lst


1)Change the timeout seconds for GRUB menu on boot-up
    * Find this quote 
...
timeout     3
...

    * Change it to: 
timeout     0

2) hide GRUB menu on boot-up

    * Find this quote: 
...
#hiddenmenu
...
    * Change it to: 
hiddenmenu

Save your /boot/grub/menu.lst

Hopefully this will work for u.

---

### Post by Ansible on 2006-11-20
hiddenmenu was already uncommented, so I just changed the timeout to 0 instead of 3.  That did the trick!  Thx for the help.

Now, supposing I wanted to select another option.  Do I just hold down ESC during boot, or what?

---

### Post by Jimmy_r on 2006-11-20
> hiddenmenu was already uncommented, so I just changed the timeout to 0 instead of 3. That did the trick! Thx for the help.

Now, supposing I wanted to select another option. Do I just hold down ESC during boot, or what?

When I have my timeout set to zero, i just tap the esc key repeadtedly from POST(the first screen you see when turning the computer on) till I get the grub menu. It is easy to miss otherwise.

---

### Post by Ansible on 2006-11-21
Ok, that worked for me too.  Thanks all for the help!

---

