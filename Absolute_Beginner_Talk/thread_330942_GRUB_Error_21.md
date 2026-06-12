---
title: "GRUB Error 21"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by weaver4 on 2007-01-03
I just installed Ubuntu and the results were disastrous.  After install I get GRUB Error 21 when I reboot.  It is a dual boot system, but I can't get to Ubuntu or Windows, computer is completely useless.

I did a search on the forum and found advise to do sudo Grub, which I did.

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

That did not fix it either.

---

### Post by meng on 2007-01-03
It may help you to post your system specs especially hard drive config, that is, how many drives, IDE/SATA, how they are partitioned, etc.

---

### Post by weaver4 on 2007-01-03
I have two drives
hd0 -- ide -- windows xp only
hd1 -- sata -- four partition
   -- windows ntfs
   -- extended partition
      -- fat 32
      -- ext3
      -- swap

---

### Post by geek_Man on 2007-01-03
Pop your Ubuntu disc in and post your menu.lst file, please. That should also help.

---

### Post by weaver4 on 2007-01-03
Here is what I found out.

If I go into my bios and disable my Legacy USB setting then GRUB will start working properly.  

But, if I do that then my GRUB will not reconize my USB keyboard so I can not select how I want it to start.  So I have the choice of it not booting or not working.

Here is the menu.lst file.

======================================

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
# kopt=root=/dev/sda7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,6)

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

title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda7 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda7 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd1,6)
kernel		/boot/memtest86+.bin 
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

---

### Post by weaver4 on 2007-01-04
I assume this is an unsolvable problem?  

Should I try a PS2 Keyboard?

---

### Post by geek_Man on 2007-01-04
That would be strange if you had to use a ps2 keyboard. Is the keyboard one of the boot options? And I'll have a look at your file.

Keep experimenting, see what you can and can't do. Try different boot orders and stuff.

---

### Post by Duck2006 on 2007-01-04
Sounds like grub is not finding your USB keyboard so i would try a PS\2 keyboard and see if you can get anything to boot

---

### Post by weaver4 on 2007-01-04
I just thought about this.  I have my usb keyboard plugged into a hub.  Could that be it?

---

### Post by geek_Man on 2007-01-04
Maybe. Try plugging your keyboard into your computer directly.

---

### Post by GrahamPR on 2007-01-04
can someone explain Error 21?

This is what I get when trying to add a cd rom boot option to grub. since installing ubuntu, I can't get back into windows to retrieve passwords and things. just seting bios to boot cdrom doesn't work. choosing safe mode in windows start up just boots me into ubuntu. 

help. :confused:

for more info see this thread.
[http://www.ubuntuforums.org/showthread.php?t=214156](http://www.ubuntuforums.org/showthread.php?t=214156)

---

### Post by Duck2006 on 2007-01-04
Grub Error 21....hard disk not found

[http://orgs.man.ac.uk/documentation/grub/grub_14.html](http://orgs.man.ac.uk/documentation/grub/grub_14.html)

---

### Post by weaver4 on 2007-01-04
Plugging the USB keyboard into the computer directly did not fix the problem.

But, using a PS2 keyboard fixed it.

What that has to do with hard disk not found I do not know.

---

### Post by geek_Man on 2007-01-04
> **weaver4 said:**
> Plugging the USB keyboard into the computer directly did not fix the problem.

But, using a PS2 keyboard fixed it.

What that has to do with hard disk not found I do not know.


That's weird. Does the keyboard have any type of (flash) drive in it?

---

### Post by geek_Man on 2007-01-04
> **GrahamPR said:**
> can someone explain Error 21?

This is what I get when trying to add a cd rom boot option to grub. since installing ubuntu, I can't get back into windows to retrieve passwords and things. just seting bios to boot cdrom doesn't work. choosing safe mode in windows start up just boots me into ubuntu. 

help. :confused:

for more info see this thread.
[http://www.ubuntuforums.org/showthread.php?t=214156](http://www.ubuntuforums.org/showthread.php?t=214156)

Graham, post your drive setup and menu.lst file.

---

