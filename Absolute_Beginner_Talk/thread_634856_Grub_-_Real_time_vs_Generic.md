---
title: "Grub - Real time vs Generic"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-12-08
ok.
What is the difference.  When I boot up, I see choices in Grub that include Realtime and also Generic in addition to WinXP.

What is the difference?

FWIW, I am trying to get Virtualbox to work.  It had been working perfectly, but, then, I tried to open XP in VB while I was playing an audio CD in Linux (Ubuntu 7.04). This locked up my computer - no mouse or keyboard control, so I rebooted.

Since then, VB will freeze if I try to start XP after having booted using the Realtime Grub selection.

After this freeze, there is no recover except by rebooting.

If, during reboot, I select the Generic option presented by Grub, I can start VB and XP loads just fine.

Just so you know, the freeze described above occurs after a faint image of the XP logon/boot-up screen appears.  Then, the computer just locks.

There are, obviously, two questions here, although I feel they may be related.

Will appreciate answers to either or both.

Caruso

---

### Post by celticbhoy on 2007-12-08
can you post the contents of /boot/grub/menu.lst

---

### Post by carusoswi on 2007-12-08
> **celticbhoy said:**
> can you post the contents of /boot/grub/menu.lst

Here it is:

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
# kopt=root=UUID=41b2eb37-06ae-49ab-8faf-89efd606f408 ro

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

title		Ubuntu, kernel 2.6.20-16-realtime
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-realtime root=UUID=41b2eb37-06ae-49ab-8faf-89efd606f408 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-realtime
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-realtime (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-realtime root=UUID=41b2eb37-06ae-49ab-8faf-89efd606f408 ro single
initrd		/boot/initrd.img-2.6.20-16-realtime

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=41b2eb37-06ae-49ab-8faf-89efd606f408 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=41b2eb37-06ae-49ab-8faf-89efd606f408 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=41b2eb37-06ae-49ab-8faf-89efd606f408 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=41b2eb37-06ae-49ab-8faf-89efd606f408 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda3
title		Microsoft Windows XP Professional
root		(hd0,2)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

---

### Post by celticbhoy on 2007-12-08
Dont really know what the runtime is, but I am guessing it really shouldnt be there. I would remove the runtime & old kernel options leaving you this from the end of the comments :-

## ## End Default Options ##

title Ubuntu, kernel 2.6.20-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=41b2eb37-06ae-49ab-8faf-89efd606f408 ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=41b2eb37-06ae-49ab-8faf-89efd606f408 ro single
initrd /boot/initrd.img-2.6.20-16-generic

title Ubuntu, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda3
title Microsoft Windows XP Professional
root (hd0,2)
savedefault
makeactive
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows NT/2000/XP (loader)
root (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1


-: This will give you two Ubuntu options, memtest, and your XP boot.

---

### Post by celticbhoy on 2007-12-08
Please note that everything before 

## ## End Default Options ##

should remain as is.

---

### Post by llamakc on 2007-12-08
The OP's menu.lst does NOT reference any "runtime" but "realtime" which is a kernel image that may be installed via Synaptic/apt-get. It is a legitimate entry in the menu.lst file.

Have you recompiled the VirtualBox kernel modules for the realtime kernel? That could be the source of your freezing up. That or VB just doesn't play well with the realtime kernel.

Also, do not edit menu.lst until you have made a backup of it.

---

### Post by carusoswi on 2007-12-08
> **celticbhoy said:**
> Please note that everything before 

## ## End Default Options ##

should remain as is.

So, I wonder, which is it?  Delete or leave all that precedes 'End Default Options'?

Caruso

---

### Post by celticbhoy on 2007-12-08
Everything that comes before leave, and alter what comes after to the above post.

---

### Post by llamakc on 2007-12-08
Doing this will remove your ability to boot into the realtime kernel, OP.

---

### Post by carusoswi on 2007-12-10
> **llamakc said:**
> Doing this will remove your ability to boot into the realtime kernel, OP.

Curious as to why I would want to remove that ability.  As things stand now, I have the choice to select real time or generic.

This isn't live or death.  I asked the question to see if I could learn more than what's already obvious - real time presents some problems, generic doesn't.  I wish someone could wise me up as to what might have gone wrong so that the real time isn't loading my wifi driver anymore.

I'm about to wipe my computer's main disc clean because I have a number of annoying issues with it.  First of all, I want to move from 7.04 to 7.10 and cannot do that until I remove the 7.04 version of Automatix.  

Secondly, due to factors I have never been able to understand, WinXP, during my last total re-installl, assigned drive letter "G" to my boot disk.  Everything works ok, but I have some applications that will not install in XP unless the OS resides on disc C . . . so, I really need to fix that condition - and the only way I know that will work is to wipe G (or perhaps that entire physical disc) clean and reinstall XP, then Ubuntu 7.10.

I was just curious how problems might have developed on my Ubuntu installation when I wasn't even connected to the 'net.

Thanks for the reply.

Caruso

---

### Post by llamakc on 2007-12-10
I don't know why you would want to remove that option, but that is what the poster who was guiding you to edit menu.lst was precisely doing.

---

