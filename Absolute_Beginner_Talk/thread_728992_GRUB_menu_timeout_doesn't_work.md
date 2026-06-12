---
title: "GRUB menu timeout doesn't work"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by jetzm on 2008-03-19
My menu timeout doesn't seem to be working.  I get a message that tells me to press 'Esc' to view the menu followed by a number.  That number is my timeout - 1, but it never actually counts down.  It just sits there waiting for me to press escape.   I can circumvent this by setting the timeout to 0 so it boots instantly but I'd like to get the countdown timer to actually work so if I ever need to I have  a few seconds to hit escape.

[This thread]("http://ubuntuforums.org/showthread.php?t=77195") talks about a splash screen and it looks like it may be an answer to my problem, but I don't actually understand it.

---

### Post by Oldsoldier2003 on 2008-03-19
> **jetzm said:**
> My menu timeout doesn't seem to be working.  I get a message that tells me to press 'Esc' to view the menu followed by a number.  That number is my timeout - 1, but it never actually counts down.  It just sits there waiting for me to press escape.   I can circumvent this by setting the timeout to 0 so it boots instantly but I'd like to get the countdown timer to actually work so if I ever need to I have  a few seconds to hit escape.

[This thread]("http://ubuntuforums.org/showthread.php?t=77195") talks about a splash screen and it looks like it may be an answer to my problem, but I don't actually understand it.

change it to a  number like "3" for 3 seconds. no signs just the number...

[http://www.howtogeek.com/howto/ubuntu/change-the-grub-menu-timeout-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/change-the-grub-menu-timeout-on-ubuntu/)

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3
```

---

### Post by jetzm on 2008-03-19
It was 3.  The only difference was there was a tab in front of it.

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

When I get to the menu it tells me to press escape followed by a 2.  If I change timeout to a different number (e.g. 7) I get that number minus one after it asks for escape.  (e.g. 6).  That number never actually counts down though.  It just perpetually waits for me to hit escape.

---

### Post by markjensen on 2008-03-19
Do you have a default?  Can you post your entire grub menu.lst file, instead of just those two small snippets?

---

### Post by Oldsoldier2003 on 2008-03-19
unless Im completely mistaken in what you are trying to say it appears to work as its supposed to work.
 grub boots to the default OS unless you hit escape and  unhide your menu . It will sit there forever waiting for your choice once you do that.

---

### Post by jetzm on 2008-03-19
I do have a default.  It's set to 0.

Even if I don't hit escape, it will sit there forever and wait for me to hit escape.

Here is my menu.lst.

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
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
# kopt=root=UUID=11f2d044-e93c-4b7f-a871-ef3dc277513a ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=11f2d044-e93c-4b7f-a871-ef3dc277513a ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=11f2d044-e93c-4b7f-a871-ef3dc277513a ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by markjensen on 2008-03-19
Other than the smiley artifacts from posting in the forum, that looks pretty straightforward.    Out of curiousity, does it timeout properly if you comment out 'hiddenmenu' ?

---

### Post by Oldsoldier2003 on 2008-03-19
> **markjensen said:**
> Other than the smiley artifacts from posting in the forum, that looks pretty straightforward.    Out of curiousity, does it timeout properly if you comment out 'hiddenmenu' ?
I would suspect that it will thats pretty much the only thing different in jetzm's grub menu .  If that doesn't fix it then its likely grub itself needs reinstall.

---

### Post by jetzm on 2008-03-19
I'm not sure.  I'll have to try it when I get back to that computer.

Incidentally, this computer used to have Windows XP on it.  For some reason, it never kept the proper time.  At first I thought it was some sort of hardware issue and that's why my timeout wasn't working.  But the clock in Ubuntu works fine, so it seems like that can't be it.

---

### Post by forrestcupp on 2008-03-19
> **jetzm said:**
> I'm not sure.  I'll have to try it when I get back to that computer.

Incidentally, this computer used to have Windows XP on it.  For some reason, it never kept the proper time.  At first I thought it was some sort of hardware issue and that's why my timeout wasn't working.  But the clock in Ubuntu works fine, so it seems like that can't be it.

I'm not sure if Ubuntu keeps time the same way.  You could need a new CMOS battery on your motherboard.

---

### Post by markjensen on 2008-03-19
> **forrestcupp said:**
> I'm not sure if Ubuntu keeps time the same way.  You could need a new CMOS battery on your motherboard.
I think you are on to it with that post right there!

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/43665](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/43665)
Shows a similar bug report.  The user that created that bug report found he also had BIOS reporting a system clock error.  He (or she) reset the battery and cleared both the clock error and the timeout problem. :)

---

### Post by jetzm on 2008-03-19
That very well may be the issue.  This was a hand me down computer so I have no idea whether the battery is good or not.

I doubt GRUB needs a reinstall as I just installed Ubuntu two nights ago for the first time.

---

### Post by jetzm on 2008-03-20
Ok, I tried it with the hiddenmenu option commented out.  Now I see the menu and at the bottom it says it will boot the highlighted option in 3 seconds.  That's it though, it just stays at 3.  I'll try changing the CMOS battery next.  Is there any way to check to see if it's bad other than physically taking it out and testing it?

---

### Post by rustutzman on 2008-03-20
Try shutting the machine off for 5 minutes then restart it and go in to BIOS. If the date and time go to their default settings the battery is dead.

Russ

---

