---
title: "grub problems"
date: 2005-10-14
forum: Absolute Beginner Talk
---

### Post by peixe on 2005-10-14
hello all,

this is my first ubuntu instalation and i'm having some problems with grub.

i've:

Windows Xp /dev/hdb1
ubuntu /dev/sda5
swap /dev/sda6

can anyone tell me how must i configure my  menu.lst file?

here is my actual file:

title: Ubuntu
root (hd0,0)
kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/sda5 ro quiet splash
initrd /boot/initrd.img-2.6.10-5-386

title Windows XP
root (hd1,0)
savedefault
makeactive
chainloader +1


when o reboot my system and try to boot ubuntu i get this error:

Error 17: Cannot mount selected partition

---

### Post by SilentCacophony on 2005-10-14
I can see two errors right off: that /dev/sda5 would eqaute to (hd0,4) for grub, and you should have *boot* at the end of a linux entry.

So:

title: Ubuntu
root (hd0,**4**)
kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/sda5 ro quiet splash
initrd /boot/initrd.img-2.6.10-5-386
**boot**

Anyway, that's not the whole file is it? Generally, it's auto-generated, and has sections for other options and such.

---

### Post by peixe on 2005-10-15
[QUOTE=SilentCacophony]
Anyway, that's not the whole file is it? Generally, it's auto-generated, and has sections for other options and such.[/QUOTE]

First of all thanks for your reply. 

i Have changed to 

title: Ubuntu
root (hd0,4)
kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/sda5 ro quiet splash
initrd /boot/initrd.img-2.6.10-5-386
boot

and works good. But here is my complete menu-lst:

title		Ubuntu 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(sd0,5)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(sd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot

title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
chainloader	+1

---

### Post by SilentCacophony on 2005-10-15
You may also want to change the following two entries so that they have the correct **root (hd0,4)** line as well, in the event that you may need them some time:

> title Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root (sd0,5)
kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/sda5 ro single
initrd /boot/initrd.img-2.6.10-5-386
savedefault
boot

title Ubuntu, kernel memtest86+
root (sd0,5)
kernel /boot/memtest86+.bin
savedefault
boot


It looks as if you may have problems if you do anything that automatically updates grub, such as installing a new kernal version, since the file is missing some of the content that is expected. Should look like so:

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda3 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title Ubuntu, kernel 2.6.10-5-386
root (hd0,4)
kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/sda5 ro quiet splash
initrd /boot/initrd.img-2.6.10-5-386
savedefault
boot

title Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/sda5 ro single
initrd /boot/initrd.img-2.6.10-5-386
savedefault
boot

title Ubuntu, kernel memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
chainloader +1

```

---

### Post by peixe on 2005-11-06
Hello again, 

When i try to boot Windows System i go to grub configurations, it opens console:

"
    GNU GRUB  version 0.95  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]

grub>
" 

Here's my menu.ls File


title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1	
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
chainloader	+1

Can someone help me?

---

