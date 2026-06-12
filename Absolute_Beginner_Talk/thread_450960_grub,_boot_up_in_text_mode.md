---
title: "grub, boot up in text mode"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by rbprogrammer on 2007-05-21
here is my /boot/grub/menu.lst:
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
# kopt=root=UUID=86c09dac-45f1-4d83-b7d7-4014dfe5198c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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
root		(hd0,6)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=86c09dac-45f1-4d83-b7d7-4014dfe5198c ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,6)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=86c09dac-45f1-4d83-b7d7-4014dfe5198c ro single
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/memtest86+.bin
quiet

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


```

what i want is when i boot up in recovery mode, that i boot up in a text mode instead of starting KDE. when i boot up in recovery mode, KDE still loads.  

now i read in some posts to do something like [FONT="Courier New"]sudo /etc/init.d/gdm stop[/FONT] or something like that for GNOME.  but i'm using Kubuntu, and i do not want to issue a command. i just want to boot into a text mode with one option and into a graphical mode with another option within GRUB.

---

### Post by louieb on 2007-05-22
I just booted to recovery mode in my Feisty Ubuntu install. Got the CLI.
I use the 20-15-generic kernel too. My recovery entry looks just like yours ending in[B] ro single. 
[/B]When you boot to using the Recovery Mode entry are you getting logged on as root? 
You got a new one on me. Maybe GRUB is screwing up.

---

### Post by rbprogrammer on 2007-05-22
> **louieb said:**
> When you boot to using the Recovery Mode entry are you getting logged on as root?

i get the option to, but i press Ctrl-D b/c i do not want to log in as root.  i guess i should try that and see if i could change to a different user,

---

### Post by ikonia on 2007-05-22
your booting into "single user mode" hence the "single" at the end of the boot line.

This does not start the run time init scripts, so the init script that launches your windows manager gnome/kde/whatever does nto get run.

---

### Post by Cypher on 2007-05-22
> **rbprogrammer said:**
> i get the option to, but i press Ctrl-D b/c i do not want to log in as root.  i guess i should try that and see if i could change to a different user,
Pressing CTRL-D says that you want to boot "Normally" which means to run all your Init scripts, one of which is to start up KDE. So why don't you login as root as that's the intended purpose..

---

### Post by rbprogrammer on 2007-05-22
all i want is in my GRUB menu to have the option to boot up text mode as just a normal user.  that has to be possible, to start text mode as a normal user?

---

### Post by louieb on 2007-05-22
Just out curiosity looked  at my Feisty servers menu.list. Boot options are the same as the Feisty Desktop.  Really don't think there is an option GRUB can pass to the kernel to tell it do a normal boot but don't start X.   (But I didn't look very hard either).
Its kinda interesting to see if GRUB could be setup to do a normal boot with separate options for GUI and the CLI.
But for now I guess you'll have to live with setting it up to boot to the CLI and typing startx when you want a GUI. Or booting to a GUI and pressing Ctrl+Alt+F1 when you want the CLI.

---

