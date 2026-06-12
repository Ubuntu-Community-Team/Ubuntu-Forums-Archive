---
title: "Switching?"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by blaunrated on 2007-07-31
Hi, i'm really liking ubuntu but there are still things on vista I want to use, and I got it to were it should daul boot but on the startup screen(when I reboot the system) it says under other OS "vista/longhorn(loader)" and when I select that all it does is restart the system.  I'm so agitated because all I want to do is listen to music(i have the X-fi card which doesn't work with linux) and play some games:mad:

---

### Post by Inxsible on 2007-07-31
> **blaunrated said:**
> Hi, i'm really liking ubuntu but there are still things on vista I want to use, and I got it to were it should daul boot but on the startup screen(when I reboot the system) it says under other OS "vista/longhorn(loader)" and when I select that all it does is restart the system.  I'm so agitated because all I want to do is listen to music(i have the X-fi card which doesn't work with linux) and play some games:mad:

did you by any chance nuke your Vista install. 
post the output of 

```
sudo fdisk -l
``` -i is lower case L

As for listening to music, you can do that easily on Linux. Go to Applications --> Add/Remove and search for GStreamer. Install all of the plugins and you should be good to go.

Games : Depends which games you wanna play.

---

### Post by st33med on 2007-07-31
True. Linux isn't for everyone, especially PC gamers. If you find yourself needing to come back to Linux, go ahead. We will still be here, we hope ;D.

---

### Post by BlueNoteExpress on 2007-07-31
I think his problem with listening to music is a sound card that doesn't work in Linux (Creative X-Fi).

---

### Post by blaunrated on 2007-08-01
Hey, i've tried what the first guy(or girl or whatever) said and I had no success, All I want to do is go back to frieken vista so I can do things I can only do on vista(without having to configure things)  Can someone please tell me a simple way to do this?  Or even a hard way I don't really care.  Like I said before when I boot the system and after it loads the grub 1.5 or whatever it shows my all of my OS selections and under "other OS(or something like that)" it shows Vista/longhorn(loader) and I've tried everything I can think of and nothing seems to work:(   someone plz help me;(

---

### Post by tchoklat on 2007-08-01
select Ubuntu at boot up, then look into your menu.lst file to see whether it is pointing to the correct partition for Vista (/boot/grub/menu.lst). If not edit it with nano (sudo nano /boot/grub/menu.lst)

OR download SuperGrubDisk, burn the ISO to CD and it can repair your bootloader to boot into windoze!

T

...then delete Ubuntu if it not 4 U!

---

### Post by blaunrated on 2007-08-01
How do I get access as a root user?  I went to administration/users_and_groups and went to the properties of mine and changed the main group to root or whatever and it still doesn't work:(

---

### Post by stevebakerj on 2007-08-01
I don't know if Vista is the same but with XP you could boot from your XP install disk and do a Fix MBR, that should fix your master boot record to what is was before Grub took over. 

As I say I don't know about Vista

---

### Post by blaunrated on 2007-08-01
I tried that, but I used to have XP and then I upgraded to vista, so all I have is an upgrade CD that you have to be in XP to work:(

---

### Post by ghanu on 2007-08-01
Hi, 

 open terminal 
 sudo gedit /boot/grub/menu.lst

This would open editor on password input.

Now look for
title "vista/longhorn(loader)"

then paste/append the following lines
root (hd0,0)
chainloader +1

save and exit
#anything following '#' is a comment, so comment the lines immediately after title "vista/longhorn(loader)" 
(hd0,0) -> first partition of ur first hard disk

Hope this helps, or try pasting ur menu.lst file if this does'nt work

---

### Post by stevebakerj on 2007-08-01
> **blaunrated said:**
> I tried that, but I used to have XP and then I upgraded to vista, so all I have is an upgrade CD that you have to be in XP to work:(

Well how about Super Grub

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Download and burn the disk then boot from it. Theres is a Windows section with Fix MBR on or if you are sure you haven't nuked your Vista install you could try to fix Grub and keep your Dual Boot option.

---

### Post by blaunrated on 2007-08-01
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
# kopt=root=UUID=8c23bc1f-c28e-4fd6-b173-0319e95a405f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8c23bc1f-c28e-4fd6-b173-0319e95a405f ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8c23bc1f-c28e-4fd6-b173-0319e95a405f ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8c23bc1f-c28e-4fd6-b173-0319e95a405f ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8c23bc1f-c28e-4fd6-b173-0319e95a405f ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
boot

---

### Post by ghanu on 2007-08-02
Ya ..there u have it..
I think u have 2 hard disks..?

replace root (hd0,0) as root (sd0,0)

or just check out before changing ie. at grub screen press 'c' 
u wud get a grub prompt: grub>
now type these ( bold font)

**root (sd0,0)**
and press 'enter' after each line
if sd0 exists the grub> reappears
continue
**chainloader +1**   --press enter
**boot **   --press enter

Now u wud b booting to ur Windozzz....:-)

Reply

---

### Post by scxtt on 2007-08-02
this is my entry for Vista which came on my laptop:
```
title Windows Vista
        rootnoverify (hd0,1)
        chainloader +1
```as far as grub is concerned, everything is hd ... you may be having problems if you have a recovery partition - so posting **sudo fdisk -l** would be helpful ...

---

### Post by ghanu on 2007-08-02
> **scxtt said:**
> as far as grub is concerned, everything is hd ... 

sorry I've gone wrong...:(

Thanx scxtt, I learnt something new :)

---

