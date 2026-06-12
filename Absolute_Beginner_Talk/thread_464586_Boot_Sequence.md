---
title: "Boot Sequence"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by sgtbob on 2007-06-04
On a dual boot system, how to get Windows to boot first? I know - I will cahnge it back to Ubuntu later, but how to make the change?

Here is the cat /boot/grub/grub.conf listing (I knew how to do this in Fedora, but it doesn't seem to be the same in Ubuntu)

bob@bob-XPS:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=5d7afe2d-0f99-4415-96c3-ba16818f41e8 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=5d7afe2d-0f99-4415-96c3-ba16818f41e8 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=5d7afe2d-0f99-4415-96c3-ba16818f41e8 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=5d7afe2d-0f99-4415-96c3-ba16818f41e8 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=5d7afe2d-0f99-4415-96c3-ba16818f41e8 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows XP Media Center Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1



Bob :(

---

### Post by Tucatts on 2007-06-04
Go here : [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

This is Grub page and I just used it to change two of my machines to boot Windows first. Not hard at all but do read it very carefully and make sure you count correctly. You will see what I am talking about. Both of my tries went great first time. Make the Super Grub disk as well. It is on the page too. That is a thing worth having!
Good luck

---

### Post by AAM on 2007-06-04
I may be wrong, but I think you just move the windows entry to the top of the choices.

---

### Post by confused57 on 2007-06-04
Try default 6, or move your Window's entry to just above the line ###BEGIN AUTOMAGIC KERNELS LIST, as described in the link Tucatts provided.

---

### Post by dpar on 2007-06-04
Do this-
In terminal type "gksudo gedit /boot/grub/menu.lst"     (without the quotes,of course)
When it opens up your menu.lst, change the Default 0  to Default 6
Save and your good to go!

---

### Post by pospam on 2007-06-05
You could also install StartUp Manager
[http://web.telia.com/~u88005282/sum/screenshots.html](http://web.telia.com/~u88005282/sum/screenshots.html)
They have a deb in their website so no hassle.
Cheers.
P

---

### Post by stefaan.dutry on 2007-06-05
I Will get you started on this, as i've been helped myself for the same thing.

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows XP Media Center Edition
root (hd0,0)
savedefault
makeactive
chainloader +1
```
This is the entry of your windows boot option (it's located at the very bottom of your page)

As you can read here:
```
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
```
You need to put it before or after AUTOMAGIC KERNEL LIST (that's currently just below this line)

So move that section to before 
```
### BEGIN AUTOMAGIC KERNELS LIST
```

And because this is now the first option in the list, (starts to count at 0), make sure the value of this line is 0
```
default 0
```

I hope this helps you, i tried to be as clear as i could:)

---

### Post by dpar on 2007-06-06
> I Will get you started on this, as i've been helped myself for the same thing.

Code:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows XP Media Center Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

This is the entry of your windows boot option (it's located at the very bottom of your page)

As you can read here:
Code:

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

You need to put it before or after AUTOMAGIC KERNEL LIST (that's currently just below this line)

So move that section to before
Code:

### BEGIN AUTOMAGIC KERNELS LIST

And because this is now the first option in the list, (starts to count at 0), make sure the value of this line is 0
Code:

default 0

I hope this helps you, i tried to be as clear as i could
__________________
How do you mean, biggest noob ever?

I'm not that big.
Reply With Quote


If you put it after    ###Begin Automatic Kernals List    it will be deleted if there is a kernel update:(

---

### Post by stefaan.dutry on 2007-06-06
> **dpar said:**
> If you put it after    ###Begin Automatic Kernals List    it will be deleted if there is a kernel update:(

I see my post may not have been clear:

It states:
> put it before or after AUTOMAGIC KERNEL LIST
And the list starts with:
```
### BEGIN AUTOMAGIC KERNELS LIST
```
and ens with:
```
### END DEBIAN AUTOMAGIC KERNELS LIST
```
so when i told it need to be before or after the list, i meant before the 
```
### BEGIN AUTOMAGIC KERNELS LIST
```
or after the
```
### END DEBIAN AUTOMAGIC KERNELS LIST
```


I appolagise for not being as clear as i could be

---

