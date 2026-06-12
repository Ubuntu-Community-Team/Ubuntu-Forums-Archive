---
title: "Grub Boot Loader"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Drifter on 2007-06-19
I followed a thread that got me up and running a dual boot with xp and ubuntu.  I installed ubuntu as master and already had xp on one drive, this is a two drive dual boot.  It all works fine except for the menu list, it has windows first but that one will not work, ubuntu is next and will work.  Windows will boot with the last line in the menu.  Question is, how to remove the first windows from the list with out messing up everything.

---

### Post by old_geekster on 2007-06-19
Run this command in the "Terminal":

gksudo gedit /boot/grub/menu.lst

You should be able to remove the first Windows entry.

---

### Post by Drifter on 2007-06-19
This is what I get when I run the command you said to do.  But how do I take the first windows off.  I don't know where to do that in the list.

title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=37b9a717-c9e8-4cbc-b30f-52cae48d5bd1 ro

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=37b9a717-c9e8-4cbc-b30f-52cae48d5bd1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=37b9a717-c9e8-4cbc-b30f-52cae48d5bd1 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=37b9a717-c9e8-4cbc-b30f-52cae48d5bd1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=37b9a717-c9e8-4cbc-b30f-52cae48d5bd1 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by bgissal on 2007-06-19
Delete this, and this only (this is at the very top):

title Windows
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

MAKE SURE THAT THE FIRST LINE IN MENU.LST READS:

# menu.lst - See: grub(8), info grub, update-grub(8)

I think you placed the command at the wrong place in the menu.

---

### Post by Drifter on 2007-06-19
OK I did that now I will reboot and check it out thanks, will let you know.

---

### Post by Drifter on 2007-06-19
I edited the very top only and now I do not get the menu when I boot only boots straight into ubuntu.

---

### Post by bgissal on 2007-06-19
Oh, I forgot. Then you need to edit your default boot system.

You need to edit the part below the line "# array will desync and will not let you boot your system".

The line below should read:

Default                  0

You need to change the 0. The new number depends on what line GRUB shows Windows XP. If you could, reboot and pay careful attention to the GRUB menu at boot. Write down, or make note of every line in this menu at boot (not in the list we just edited). Please post the lines. Then I'll tell you what number should go in place of the "0."

---

### Post by bgissal on 2007-06-19
Just to be perfectly clear, make sure to count the line "other operating systems"... that is if there is one.

---

### Post by Drifter on 2007-06-19
When I boot now it doesn't list the menu it just goes on into ubuntu.

---

### Post by bgissal on 2007-06-19
Does it show the GRUB boot menu at all?

---

### Post by Drifter on 2007-06-19
> **bgissal said:**
> Oh, I forgot. Then you need to edit your default boot system.

You need to edit the part below the line "# array will desync and will not let you boot your system".

The line below should read:

Default                  0

You need to change the 0. The new number depends on what line GRUB shows Windows XP. If you could, reboot and pay careful attention to the GRUB menu at boot. Write down, or make note of every line in this menu at boot (not in the list we just edited). Please post the lines. Then I'll tell you what number should go in place of the "0."

I do not have a boot menu at boot now it boots into ubuntu only with no other choices.

---

### Post by bgissal on 2007-06-19
Oh sorry. I didn't read your whole post. I am going to restart my machine just to see for myself. In the meantime, just put 6 in place of the zero.

---

### Post by Drifter on 2007-06-19
> **bgissal said:**
> Does it show the GRUB boot menu at all?

No it does not show grub at all it says booting grub but then it counts down to 0 and goes into ubuntu there is no list at all

---

### Post by bgissal on 2007-06-19
Now I see what you mean. My machine is similar. If you didn't get it already, you have to hit ESC before the countdown gets to zero.

---

### Post by Drifter on 2007-06-19
OK let me try that and I will let you know.

---

### Post by Drifter on 2007-06-19
> **bgissal said:**
> Now I see what you mean. My machine is similar. If you didn't get it already, you have to hit ESC before the countdown gets to zero.

Ok esc gets it done, question is do I need to hit esc everytime to get to the menu.  If I put 6 in the place of the 0 would xp then boot like unbuntu does now.

---

### Post by pxwpxw on 2007-06-19
I think the problem is here


# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

---

### Post by bgissal on 2007-06-19
Assuming that the GRUB says:

Linux Kernel blah blah blah
Linux Kernel (recovery) blah blah blah
Linux Kernel blah blah blah
Linux Kernel (recovery) blah blah blah
memtest blah blah blah
Other operating systems:
Windows XP

You want the line number 6 for a default boot in XP. Remember that in 'puter language that all numbers start with 0 and not 1. Even though Windows XP is on the 7th line in ordinal numbers (1,2,3..etc.), you need to have 6. Yes you would need to hit esc every time you would want to boot into ubuntu. If you find (HOPEFULLY) that Windows is a piece of crap, then just change the default back to zero.

---

### Post by Drifter on 2007-06-19
I don't think I will change so xp will be first I was just wondering if that would be the case.  Xp is 5 on my list I don't have boot other os's

---

### Post by bgissal on 2007-06-19
I have another suggestion. When I have a dualboot, I like to change the time available to hit ESC. This is where the lines come into play to change it. 

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3 

I find 3 seconds to be too short to react to hitting escape with a dualboot, so I usually ramp it up to 7 or so. It may elongate the boot time by 7-3=4 seconds. But you'll still be in pretty good shape. If I hit escape early enough, I like to use the saved time by cursing Windows for their Darwinian ways and monoplostic tendencies.

---

### Post by Drifter on 2007-06-19
> **bgissal said:**
> I have another suggestion. When I have a dualboot, I like to change the time available to hit ESC. This is where the lines come into play to change it. 

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3 

I find 3 seconds to be too short to react to hitting escape with a dualboot, so I usually ramp it up to 7 or so. It may elongate the boot time by 7-3=4 seconds. But you'll still be in pretty good shape. If I hit escape early enough, I like to use the saved time by cursing Windows for their Darwinian ways and monoplostic tendencies.

Yes I did change that to 5 secs. to give more time to hit esc

---

