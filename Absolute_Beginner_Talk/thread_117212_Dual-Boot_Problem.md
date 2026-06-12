---
title: "Dual-Boot Problem"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by babyfair on 2006-01-14
Installed Windows XP first followed by Ubuntu. Ubuntu boots with no problems, but after booting windows from grub, it shows the boot splash, and suddenly restarts with no error message. There are two hard disks and Windows is on hda (hd0,0)

menu.1st:
[PHP]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=/dev/hdb2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

[/PHP]

---

### Post by amohanty on 2006-01-14
> but after booting windows from grub, it shows the boot splash, and suddenly restarts with no error message

So are you able to boot into windows at all or does this happen _after_ a successful windows session?

AM

---

### Post by me3ohm on 2006-01-14
Hi,

Are you booting Windows from full Power Off, or restarting the computer (i.e. Windows reboots or restarting Ubuntu)?

I have seen some Google hits that comment that a similar problem allows Windows to boot if the computer is switched off fully, and then powered on - selecting Windows from the Grub menu.

I don't know if this will help - but worth a try!

Matthew

---

### Post by babyfair on 2006-01-15
[QUOTE=amohanty]So are you able to boot into windows at all or does this happen _after_ a successful windows session?

AM[/QUOTE]
nope, i'm unable to boot into windows at all.. only able to see it load for a while and it auto reboots

---

### Post by babyfair on 2006-01-15
[QUOTE=me3ohm]Hi,

Are you booting Windows from full Power Off, or restarting the computer (i.e. Windows reboots or restarting Ubuntu)?

I have seen some Google hits that comment that a similar problem allows Windows to boot if the computer is switched off fully, and then powered on - selecting Windows from the Grub menu.

I don't know if this will help - but worth a try!

Matthew[/QUOTE]

thx, but i'm still unable to boot to windows wif either ways..

---

### Post by peanut butter on 2006-01-15
between reboots try waiting 7 min it might be that your memory is full. i remember those days.

---

### Post by babyfair on 2006-01-15
[QUOTE=peanut butter]between reboots try waiting 7 min it might be that your memory is full. i remember those days.[/QUOTE]

I tried again e next day but to no avail.

---

### Post by peanut butter on 2006-01-15
is that your whole menu.list if not can u please post the whole thing?

edit: sorry i dident see the scroolbar

---

### Post by peanut butter on 2006-01-15
is that after the windows loading screen starts or before?

---

### Post by babyfair on 2006-01-15
[QUOTE=peanut butter]is that after the windows loading screen starts or before?[/QUOTE]

It was partialy loading windows.. as in not e GUI interface

---

### Post by peanut butter on 2006-01-15
i am sorry to say this but this dosent seem to be because of ubuntu or grub.
and i dont see anything wrong with your menu.lst

---

### Post by babyfair on 2006-01-15
[QUOTE=peanut butter]i am sorry to say this but this dosent seem to be because of ubuntu or grub.
and i dont see anything wrong with your menu.lst[/QUOTE]

But previously, i've tried dual boot wif Fedora and it works..

---

### Post by amohanty on 2006-01-15
> nope, i'm unable to boot into windows at all.. only able to see it load for a while and it auto reboots

Is there any error message (it might just flash by.. win :) eh - what can you do )?

AM

---

### Post by me3ohm on 2006-01-19
How about safe mode?  If you press F8 immediately after Grub starts to load Windows, you will have a Windows menu appear - Select Safe mode.   

If it loads correctly in Safe mode - It's a Windows issue and as said before - it is not easy to see whats going on.  

If you do get into safe mode but it still won't boot normally - go into Safe mode again and goto Control panel/System and on the Advanced tab, click the Error Handling (?)  and remove the tick in Automatically restart - you might get to see a dump message showing possibly a missing file etc.

Worth a try anyway!

Matthew

---

