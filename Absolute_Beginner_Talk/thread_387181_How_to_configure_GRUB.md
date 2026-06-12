---
title: "How to configure GRUB"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Majin Zero on 2007-03-18
How can I edit the wait time till it auto selects?

Also how can I add other stuff to it? I heard you can put disk images into it so you can have a DOS floppy image in case you'd ever need to boot to DOS

And let me know of any other neat tricks/tips there are for GRUB

---

### Post by fusiachi on 2007-03-18
For the first question,
```
sudo gedit /boot/grub/menu.lst
```
What you want to edit is "Timeout"; it's pretty well documented.

---

### Post by Majin Zero on 2007-03-18
thanks.

Anyone know about the other stuff?

---

### Post by fusiachi on 2007-03-18
Well, to boot to a disk image, you'd just add the appropriate entry to **menu.lst**.
This [thread]("http://ubuntuforums.org/showthread.php?p=2195208") gives an example of how to do something similar.  I'm sure it can be applied to your situation.

---

### Post by Majin Zero on 2007-03-18
thanks dude, that's what I wanted to do.

Hmm, any other neat tricks or things I should know about grub?

---

### Post by fusiachi on 2007-03-18
Nothing that comes to mind.

In most cases, the answer lies within **/boot/grub/menu.lst**

---

### Post by Majin Zero on 2007-03-18
gedit not found.

I should note that I'm in Xubuntu. What's the alternative in Xubuntu?

---

### Post by mahiyar on 2007-03-18
try nano.

---

### Post by fusiachi on 2007-03-18
Presumably vim or nano.

```
sudo nano /boot/grub/menu.lst
```

I forget the default graphical editor in xubuntu... It might be **mousepad**?

---

### Post by Majin Zero on 2007-03-18
It was mousepad.

---

### Post by Johnnie_Walker on 2008-06-21
To avoid opening another thread, I will ask it here. I put on the same hard *Fedora 9* to try it, but its own boot loader had the only option in the grub: Fedora e.t.c. I have *Winbuzz* and *ununtu 8.04* as well, but they don't exist for Fedora. I managed to repair my grub with my good old friend - *super GRUB disk*, but now the Fedora option doesn't exist.

My questions are:
1. How should I configure the loader, so that I can run my three OSs?
2. How to remove older(pre update) versions of ubuntu from the menu like:
> 
Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)

Ubuntu 8.04, kernel 2.6.24-16-generic

Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)

This is how my *menu.lst* looks like:
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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		15

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
# kopt=root=UUID=dd0d8eb0-770f-4f65-9a8c-50cb7c998443 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=dd0d8eb0-770f-4f65-9a8c-50cb7c998443 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=dd0d8eb0-770f-4f65-9a8c-50cb7c998443 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=dd0d8eb0-770f-4f65-9a8c-50cb7c998443 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=dd0d8eb0-770f-4f65-9a8c-50cb7c998443 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=dd0d8eb0-770f-4f65-9a8c-50cb7c998443 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=dd0d8eb0-770f-4f65-9a8c-50cb7c998443 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
rootnoverify
```

---

### Post by logos34 on 2008-06-21
1. [http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile](http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile)


2. [http://users.bigpond.net.au/hermanzone/p15.htm#_howmanyall](http://users.bigpond.net.au/hermanzone/p15.htm#_howmanyall)

or comment out (hash '#') older entries

---

### Post by Johnnie_Walker on 2008-06-21
> **logos34 said:**
> 1. [http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile](http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile)


2. [http://users.bigpond.net.au/hermanzone/p15.htm#_howmanyall](http://users.bigpond.net.au/hermanzone/p15.htm#_howmanyall)

or comment out (hash '#') older entries
The second one is fixed thanks to you, but I can't figure out what exactly should I write, in order to add *Fedora 9*. I am really newbie in working with linux and the possibility to mess something up is really big :)

---

### Post by logos34 on 2008-06-21
what partition is fedora on?

---

### Post by Johnnie_Walker on 2008-06-21
> **logos34 said:**
> what partition is fedora on?
/dev/sda1   *        7905        8944     8353792   83  Linux

It is the only one with a star, if it matters to you.

---

### Post by logos34 on 2008-06-21
reopen men.lst as root:

**gksudo gedit /boot/grub/menu.lst**

try putting this at the bottom:

> title        Fedora 9
configfile   (hd0,0)/boot/grub/menu.lst

the '*' is a boot flag (not really needed for linux)

---

### Post by Johnnie_Walker on 2008-06-21
> **logos34 said:**
> reopen men.lst as root:

**gksudo gedit /boot/grub/menu.lst**

try putting this at the bottom:



the '*' is a boot flag (not really needed for linux)

i thought about doing this, but aren't the detail like this:
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic [COLOR="Red"]root=UUID=dd0d8eb0-770f-4f65-9a8c-50cb7c998443 ro quiet [/COLOR]splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
needed?
However, I will try it now :)

---

### Post by logos34 on 2008-06-21
you can certainly use the longer version--simply mount your fedora partition and copy the entry from the latter's menu.lst

---

### Post by Johnnie_Walker on 2008-06-21
It didn't work the first way you told me. An error occured: invalid or not executable disk.

I even changed it to:
```
title       Fedora 9
root        (hd0,1)
kernel      /media/_1/boot/vmlinuz-2.6.25.6-55.fc9.i686
```
, but no success.

The trick with hiding older ubuntu kernels didn't help by changing:
```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=[COLOR="DarkOrange"]1[/COLOR]

```

Will it help, if I just del the rows with older versions or change something else to remove them?

---

### Post by logos34 on 2008-06-21
After you change 'howmany=' run **sudo update-grub**

Or just put a '#' in front of each line in each of the stanzas for the older kernels. Or delete them like you say. It's all on the page link I gave you.

If fedora is on the first disk partition, then (hd0,0) should work.

Try the chainloader entry:

> title        Fedora
root        (hd0,0)
chainloader    +1

Or the full entry from fedora's menu.lst, as I suggested above.  

You might also try installing grub to the boot sector of the fedora root partition, maybe that will help:
> 
[B]sudo grub

grub> find /boot/grub/stage1[/B]
(it should output 'hd0,0' and 'hd0,3')
[B]grub> root (hd0,0)
grub> setup (hd0,0)
grub> quit[/B]

---

### Post by meierfra. on 2008-06-21
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)

This seems to say that Windows is on (hd0,0)

So I advice against "setup (hd0,0)" until  we really know where Fedora is located.

(If Windows is on (hd0,0), this would erase the Windows boot sector)

But of course, "find /boot/grub/stage1 " will no return "(hd0,0)" is this case.

---

### Post by logos34 on 2008-06-21
> **Johnnie_Walker said:**
> /dev/sda1   *        7905        8944     8353792   83  Linux

Please post the whole fdisk output. (you didn't say anything about windows and I missed it at the very bottom of menu.lst)

Also, what does gparted show (screenshot)?

---

