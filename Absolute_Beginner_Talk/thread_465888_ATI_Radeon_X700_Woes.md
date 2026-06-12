---
title: "ATI Radeon X700 Woes"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2007-06-06
I thought I had this licked, but I seem to be having problems again with my ATI Radeon X700 video card.

I have installed 7.04 Feisty Fawn x64 from the alternate CD using the text setup.

The installations seems to have gone fine, and booting to the recovery console is no problem.

However once again, I'm tripping up when i'm trying to get the X server running.

Previously on Edgy, I got it working by doing some of these (sorry, I can't recall the exact combination I used)

apt-get install xorg-driver-fglrx followed by dpkg-reconfigure xserver-xorg / choose fglrx driver

sudo vi /etc/X11/xorg.conf, edit 'ati' to 'vesa' in the ATI card section, then (!w) save

I'm not sure if I'm missing something out this time, or doing something I shouldn't..

In an attempt to clear possible past 'mistakes' I tried to delete xorg.conf and backups:

unlink xorg.conf
unlink xorg.conf.20070606110013.. & a few other backups

dpkg-reconfigure xserver-xorg always seems to produce a new xorg.conf, but the weird thing (to me) is that it always seems to know my previous attempts settings even though I deleted the .conf files - so clearly there's something basic I'm not understanding there, at least.

Wondered if anyone might hazard a guess at what I should do to get my GUI back?




[edit]



okay, I ran:

sudo apt-get --reinstall install xorg

then

sudo apt-get install xorg-driver-fglrx

then

sudo dpkg-reconfigure xserver-xorg again, again choosing the fglrx driver


now, I can type 'startx' at the recovery mode prompt, and all's fine & dandy, GUI comes up, everything's fine

however when I try to boot up the system normally, it still dies to a black screen.


[edit]


tried the suggestions at [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

still no joy as yet.

---

### Post by dstew on 2007-06-06
Post the contents of your /boot/grub/menu.lst file. You might have a boot option that is messing up your GUI in your kernel line.

---

### Post by ecs_pf5 on 2007-06-06
Ok here it is;

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
#      password --md5 
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
# kopt=root=UUID=fcd81e70-485b-41cf-8df0-043087c4dd1a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fcd81e70-485b-41cf-8df0-043087c4dd1a ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fcd81e70-485b-41cf-8df0-043087c4dd1a ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=fcd81e70-485b-41cf-8df0-043087c4dd1a ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=fcd81e70-485b-41cf-8df0-043087c4dd1a ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,4)
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

```

---

### Post by wcbardwell on 2007-06-06
I have an ATI X600 in my machine and am running 7.04. I selected ATI under the driver list and it works beautifully. hope it helps.

---

### Post by ecs_pf5 on 2007-06-06
I modified it thus:

```

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fcd81e70-485b-41cf-8df0-043087c4dd1a ro
initrd		/boot/initrd.img-2.6.20-16-generic
#quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fcd81e70-485b-41cf-8df0-043087c4dd1a ro single
initrd		/boot/initrd.img-2.6.20-16-generic

#title		Ubuntu, kernel 2.6.20-15-generic
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.20-15-generic #root=UUID=fcd81e70-485b-41cf-8df0-043087c4dd1a ro quiet splash
#initrd		/boot/initrd.img-2.6.20-15-generic
#quiet
#savedefault

#title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.20-15-generic #root=UUID=fcd81e70-485b-41cf-8df0-043087c4dd1a ro single
#initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

```

i.e. I removed 'quiet splash' from the root= line, commented out the line that just says 'quiet', and commented out all the 2.6.20-15 references entirely.

It now boots perfectly, except that you get all the command line stuff racing past. I don't mind that.

It doesn't seem to have remembered any of my settings / firefox favourites etc etc from when I was booting via recovery mode though. I guess that's normal because I'm now using my proper account, right? Was I root or something, in recovery console kludge-GUI?

Guess it's 99% sorted. Just that nagging curiousity left as to what exactly the problem actually is.

---

### Post by ecs_pf5 on 2007-06-06
Sorry wcbardwell, crossed post - thanks for the info, I'll have a play with that :)

---

### Post by dstew on 2007-06-06
Menu.lst is OK. Do you get the splash screen when you boot the regular kernel? Do you get to the login screen? If startx works from the recovery mode, it probably means that you have the correct GUI specified for yourself as a user, but not for the system as a whole. This can happen if you make changes to local scripts or other administrative settings as a user, but not as a superuser. We can probably figure out what to do.

EDIT: Just saw your post. Probably best to keep it as is for now. If you want to do the detective work to figure out exactly why it was having a problem before, we can do it, but maybe just let it rest.

---

### Post by kittyhawk63 on 2007-06-06
This is a mere suggestion. After trying a number of things, I found that changing ati in xorg.conf to vesa fixed my crashing and screen freezes. I have an ATI Radeon 9200SE video card. This may not work for your card. I have less screen resolutions, but it is okay. I have the one that I would choose anyway. You could give it a try.

Here is the line that I changed in xorg.conf:
Section "Device"
    Identifier    "ATI Technologies Inc RV280 [Radeon 9200 SE]"
    Driver        "[COLOR=Red]vesa[/COLOR]"
    BusID        "PCI:0:3:0"
EndSection

If you try it, remember to log out and log back in.
kh

---

### Post by ecs_pf5 on 2007-06-06
I don't get the splash screen or login screen at all when booting regular - it just goes black & there is a monitor firmware message 'no signal'.

> 
If startx works from the recovery mode, it probably means that you have the correct GUI specified for yourself as a user, but not for the system as a whole. This can happen if you make changes to local scripts or other administrative settings as a user, but not as a superuser


That sounds suspicious - I'm almost certain that the very first time I ran dpkg-reconfigure xserver-xorg, I failed to sudo before it... ?

kittyhawk thanks for the suggestion :)

---

