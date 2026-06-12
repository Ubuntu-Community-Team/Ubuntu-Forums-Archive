---
title: "How to save after editing grub bootloader?"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by atarileaf on 2006-12-25
I wanted to take a line out of my grub when it boots up. Its a line I was told in another thread might be causing my tty error. The line is break=bottom. 

Now when it boots, it says press e for edit, which I can do, but I see no command to save the changes. If I hit return or exit the line is still as it was before so how do I save the changes when I'm editing at the grub boot loader?

---

### Post by Mazen on 2006-12-25
are you able to boot you system? if yes ( or just boot in recovery mode)
go ```
sudo nano /boot/grub/menu.list
``` and edit that removing the line you want and then exit and save (Ctrl+X to exit and then Y to save) it will ask you

---

### Post by atarileaf on 2006-12-25
Wow, very quick. Thank you! :D

---

### Post by atarileaf on 2006-12-25
Strange, when I input that command in my terminal, nothing comes up. Just the terminal window with no data or code, just the commands at the bottom, like this:

 GNU nano 1.3.12          File: /boot/grub/menu.list  










                                 [ New File ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

---

### Post by Mazen on 2006-12-25
mmm...weird...well if you're IN ur ubuntu, do ```
gksudo gedit /boot/grub/menu.list
``` it should open it in gedit then edit it

---

### Post by pistcivet on 2006-12-25
Its: sudo gedit /boot/grub/menu.lst
But I think you should post the whole file and say which line(s) you are planning to delete.

---

### Post by Mazen on 2006-12-25
wo wo sorryy it's menu.lst!! dumb typo error!

---

### Post by atarileaf on 2006-12-25
> **pistcivet said:**
> Its: sudo gedit /boot/grub/menu.lst
But I think you should post the whole file and say which line(s) you are planning to delete.

Good idea. If anyone can see any lines that could give me boot problems that would cause the tty error, please let me know:
> 
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
# kopt=root=UUID=0d495912-46f1-4bd0-bc9c-11359cc79c76 ro
# kopt_2_6=root=/dev/hdb1 ro

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
# defoptions=quiet splash break=bottom

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash break=bottom
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,0)
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
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by pistcivet on 2006-12-25
The only part I see different than mine is "break=bottom"
Here's a bit of my (Dapper) menu.lst:```
title           Ubuntu, kernel 2.6.15-27-k7
root            (hd0,8)
kernel          /boot/vmlinuz-2.6.15-27-k7 root=/dev/hda9 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-k7
savedefault
boot
```I don't think it would hurt to change that one line. (remove break=bottom)
Maybe wait for someone more knowledgeable though.

---

### Post by atarileaf on 2006-12-25
That worked! :D 

Removing the break=bottom command got rid of the busybox tty error! :D 

To explain how it got there. I was one of the many (it seemed) who had the unfortunate problem of owning an ATI card that seemed to force the LiveCD to freeze to a blank screen as it loaded. The answer was to hit F6 and add the break=bottom command to allow me to change the xorg.conf to say "vesa" instead of "ati".

Once I actually loaded Ubuntu onto my hard drive, the installation seemed to have kept the break=bottom command and was therefore giving me the "/bin/sh; can't access tty; job control turned off" error every time I booted through GRUB. If I typed "exit" it would boot but removing that break=bottom seemed to have corrected that.

Does that sound like the correct assumption as to what happened in my case? If anyone else is having a similar problem, this may fix it for you. 

Thanks again for your help everyone!
:D

---

