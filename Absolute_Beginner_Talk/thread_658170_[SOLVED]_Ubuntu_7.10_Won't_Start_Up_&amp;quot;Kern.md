---
title: "[SOLVED] Ubuntu 7.10 Won't Start Up &amp;quot;Kernel Panic&amp;quot;"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by tim237 on 2008-01-04
Hey guys,

Just started my computer and I got this error message:


Starting up...

[   17.894410] RAM DISK: ran out of compressed data
[   17.894466] invalid compressed format (err=1)
[   17.895094] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block(0,0)


 This means I can't load my computer, I'm currently running off a Live CD. Help! I'm running Gutsy on a Toshiba Equium L10-300. I don't know what system specs might be helpful so if you need any do say. Also in case this has any relevance I'm not dual booting and the last time I was on my computer I had to manually turn of the computer because the quit button wasn't working.

Please help guys only had Ubuntu for a week :(

---

### Post by charlie763 on 2008-01-04
What are the RAM specs on your machine? I originally thought you may not have enough RAM, but after searching for that model on Google, it seems like it should run Gutsy just fine. Now I'm thinking you may have some bad RAM. There may be some section of the RAM that the live CD appears to write to, but cannot read from due to some hardware failure.

You can use the live CD to test your RAM. I think it's the second to last option on the list.

---

### Post by tim237 on 2008-01-04
Says I've got 495M cashed and 17M reserved.

---

### Post by charlie763 on 2008-01-04
That's definitely enough RAM. The only suggestion I have is to run the memory test. It may take a few hours. Sorry I can't be of more help. Good luck.

---

### Post by tim237 on 2008-01-05
Thanks for trying. I've run it through once and nothing showed up but I'll probably have another try just in case. There seems to be a lot of stuff on the same problem on this post, [http://ubuntuforums.org/showthread.php?t=576087]("http://ubuntuforums.org/showthread.php?t=576087"), but all of it goes WAY over my head. If there are any newbie translators out there their assistance would be welcome!

Just to add I've tried opening in the system recovery mode by pressing escape during the load and I get exactly the same thing. I can open the terminal and all that as well to edit the code for the start up, but I have no idea what I'm doing. If they help anyone sort it, that'd be awesome!

---

### Post by tim237 on 2008-01-05
Sorry to be a pest but has anyone got any ideas. I've been at it all day and not success

---

### Post by charlie763 on 2008-01-05
I took a look at the thread you linked to. It looks like people are having trouble with the menu.lst. Post your /boot/grub/menu.lst and I'll take a look at it.

---

### Post by tim237 on 2008-01-06
hear you go:

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
# kopt=root=UUID=4eaba1ab-aba6-44e4-9cbd-82db81f4faa0 ro

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4eaba1ab-aba6-44e4-9cbd-82db81f4faa0 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4eaba1ab-aba6-44e4-9cbd-82db81f4faa0 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Thanks so much!

---

### Post by tim237 on 2008-01-08
Well guys, thank you very much for your help, especially charlie763. I found a way to back up my data and then I reinstalled and it seemed to sort itself out. Haven't a clue what caused it, hopefully it won't happen again. Thanks anyway!

P.S. If you find this page and you want to know how to back up your data so you can reinstall see: [http://ubuntuforums.org/showthread.php?t=658971](http://ubuntuforums.org/showthread.php?t=658971) . I'd advise you update that software manually. I decided to just copy and past my old /root straight into my new one. Computer really didn't like that and I had to reinstall.

---

### Post by ghindo on 2008-01-16
Bumping this thread because I'm having the exact same problem.

I'm running Gutsy with 2 GB of RAM.  I started getting this message after I installed KDE4.  

Fortunately, I'm able to just boot off of an older kernel, but it's still annoying nonetheless.  

How do I solve this?  More importantly, how do I file a bug about this?

---

### Post by ghindo on 2008-01-17
Bump.  I googled around a bit looking for answers and it seems that they are all dead ends.  I don't want to re-install unless absolutely possible - can anybody help me out?

---

### Post by ghindo on 2008-01-17
Bump.

---

### Post by ghindo on 2008-01-18
Bump.  Should I try recompiling the kernel?  If so, how do I do that?

---

### Post by ghindo on 2008-01-21
Nevermind.  Fixed my problem.  It turns out that something with KDE4 did not sit well with my machine, so uninstalling it fixed it.

---

