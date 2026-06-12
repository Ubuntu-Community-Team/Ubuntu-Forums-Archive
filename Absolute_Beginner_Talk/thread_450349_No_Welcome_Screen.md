---
title: "No Welcome Screen"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by weaver4 on 2007-05-21
I do not get a welcome screen when I boot.  The screen goes completely blank from Grub until I get the login screen.  I am sure it is a screen refresh rate problem.  My LCD monitor is 1024x768 at 60hz.   What file, and parameter, do I need to modify to correct this problem.

---

### Post by apjone on 2007-05-21
this will be a setting in /boot/grub/menu.lst

you will need to add splash to the end of the kernel line I think.

---

### Post by Outrunner on 2007-05-21
First make a backup

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bk
```

then ```
gksudo gedit /etc/X11/xorg.conf
``` to edit your xorg config

To be honest I don't think this will solve your problem, but since you asked... Here's a HOWTO anyway [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by weaver4 on 2007-05-21
I tried to edit the menu.lst file by setting the vga code to 791 (vga = 791) but the spash screen is still not there.  I don't think the problem is the resolution but I think it has set the refresh rate to 75hz and I need to set it to 60.

---

### Post by weaver4 on 2007-05-21
None of these ideas worked.

How do I tell Ubuntu to use 60hz only for the splash screen?

---

### Post by apjone on 2007-05-21
post your /boot/grub/menu.lst here

---

### Post by weaver4 on 2007-05-22
Here it is.
=============================
[FONT="Courier New"]
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
# kopt=root=UUID=47904c33-fdbb-490f-9de2-a089a4d2dec5 ro

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=47904c33-fdbb-490f-9de2-a089a4d2dec5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=47904c33-fdbb-490f-9de2-a089a4d2dec5 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST[/FONT]

---

### Post by wormser on 2007-05-22
Did you change your log on screen?  I changed mine and the wrong one is displayed.  Plus I lost the shut down option when going to shut down.  I think there are some bugs involved.  Which version are you running?

Check to see the Enable Automatic Login is not checked.  System> Administration> Login Window> Security tab.

---

### Post by weaver4 on 2007-05-22
I did not change my logon screen.

Auto login is not enabled.  But the logon screen works fine.  

It is the screen that shows Ubuntu and a progress bar that I do not have.  Once that is over and I get to the logon screen all works well.

---

