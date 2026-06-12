---
title: "Can't boot into ubuntu after acronis disk director downgrade"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by Nazgulled on 2006-03-14
I installed acronis disk director (with os selector) v10 on a laptop, but I was having lots of problems, it seems very buggy and slower related to v9 so I downgrade to v9, which I wasn't having any problems whatsover...

Anyway, I had windows xp and ubuntu linux installed on my machine and they both appeared in os selector, after the downgrade, I only see windows xp, I can't boot into ubuntu now... any ideas?

---

### Post by Pragmatist on 2006-03-14
From the Acronis website FAQ: [http://www.acronis.com/homecomputing/products/diskdirector/faq.html#n34](http://www.acronis.com/homecomputing/products/diskdirector/faq.html#n34)
> [SIZE=2]
**I already have Acronis OS Selector installed, and I would like to install Linux on my computer. Where should I install the Linux loader: to MBR or to the boot sector of the partition? Maybe I do not have to install it at all?**[/SIZE] Acronis OS Selector does not substitute the Linux loader, so you should install the Linux loader (usually GRUB or Lilo) to the boot sector of the partition you plan to install Linux itself.
 
This means that GRUB still matters.  How did you set up Acronis the first time?  How do you get into your Linux system for administration without Acronis?

---

### Post by Nazgulled on 2006-03-14
First I installed ubuntu and configured to work with grub during the installation process... after rebooting and all that, I had the grub menu to choose which OS I wanted to load, winxp was there of course... I didn't change anything to this point...

I then booted into windows and installed os selector, after rebooting, os selector pops up with 2 entries, one for windows and another for linux, if I booted into the linux one, the grub menu shows up allowing me once more to chose which OS to load... so, I edited the menu.lst file of grub and disabled the menu prompt so it would load the default OS (which was ubuntu).

After that, I just had to choose from windows or linux on os selector and they booth worked, if I choose linux, grbu will automatically boot into ubuntu and that's how I want it to work.

Then, as v10 was pretty buggy and slower, I uninstalled it and installed v9, that's when, os selector only shows windows xp and not a linux entry. I don't believe that it's not compatible with that version...

---

### Post by Pragmatist on 2006-03-14
What is your partition layout?  Did you put GRUB in the MBR or in a boot partition?

---

### Post by Nazgulled on 2006-03-14
I don't really remember... but I only configure that during the install process and I don't remember doing any changes, I basically answered "next", "next"... on that part of the setup

---

### Post by Pragmatist on 2006-03-14
You could use a boot disk or a LiveCD like Knoppix to  re-install grub and  see what happens.  Send  us a copy of the /boot/grub/menu.lst file

---

### Post by Nazgulled on 2006-03-15
I have both the install and livecd from ubuntu 5.10, can I reinstall grub with any of those? How?

I'm going to use Explore2fs so I can get the menu.lst file from the linux partition from windows... hope it works.

---

### Post by Nazgulled on 2006-03-15
here's the menu.lst file:

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

## If you want special options for specifiv kernels use kopt_x_y_z

## where x.y.z is kernel version. Minor versions can be omitted.

## e.g. kopt=root=/dev/hda1 ro

# kopt=root=/dev/hda4 ro



## default grub root device

## e.g. groot=(hd0,0)

# groot=(hd0,3)



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



title		Ubuntu, kernel 2.6.12-9-386 

root		(hd0,3)

kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda4 ro quiet splash

initrd		/boot/initrd.img-2.6.12-9-386

savedefault

boot



title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)

root		(hd0,3)

kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda4 ro single

initrd		/boot/initrd.img-2.6.12-9-386

boot



title		Ubuntu, memtest86+

root		(hd0,3)

kernel		/boot/memtest86+.bin  

boot



### END DEBIAN AUTOMAGIC KERNELS LIST



# This is a divider, added to separate the menu items below from the Debian

# ones.

title		Other operating systems:

root





# This entry automatically added by the Debian installer for a non-linux OS

# on /dev/hda2

title		Microsoft Windows XP Home Edition

root		(hd0,1)

savedefault

makeactive

chainloader	+1


```

---

### Post by Pragmatist on 2006-03-15
I see you have ubuntu on /dev/hda4 and windows on /dev/hda2  What is on /dev/hda1  In general, what does your partition table look like.  You can use the LiveCD to run ```
fdisk
``` and print the partition table.  Also, try these howtos out and see if they help.  If not, come back and we'll work through it together:

[https://wiki.ubuntu.com/GrubHowto?highlight=%28grub%29](https://wiki.ubuntu.com/GrubHowto?highlight=%28grub%29)
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub)
[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29)

If I missed anything, you can check out: [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)
and type in keyword **grub**

---

### Post by Nazgulled on 2006-03-16
on hda1 there's a recovery partition from asus for windows... it's not my laptop, so I left it there...

I'll try to get into those documents in the wiki and I belive I'll be able to fix it... but I will only know that in the next week cause these problems are on my friend's laptops and for this week, university is over lol...

thanks, I'll let you know later...

---

### Post by Nazgulled on 2006-03-18
weee, I was able to fix one, thanks a lot :)

---

