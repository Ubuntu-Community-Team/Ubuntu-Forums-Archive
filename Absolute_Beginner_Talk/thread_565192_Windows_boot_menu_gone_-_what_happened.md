---
title: "Windows boot menu gone - what happened?"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by nwkegan on 2007-10-02
Oh boy, I hope I didn't make a huge mistake. I haven't come on my linux partition in a while, and basically my grub menu has windows on top and then linux on the bottom. However, when I restarted after installing updates, the kernels that were below it were also above the divider where windows is supposed to be.  How do I get the windows boot menu list back so I can boot up. I'll also be sure to change the default selected boot menu next time instead of just rearranging them.

Thanks for anyones help.

---

### Post by nwkegan on 2007-10-02
Okay, so I tried reinstalling grub but that did not restore my windows menu option.

How do I figure out what I need to put in menu.lst so I can once again boot on windows?

---

### Post by dpar on 2007-10-02
Do you mean that Windows isn't even listed or that it just isn't in the right order?

---

### Post by nwkegan on 2007-10-02
Not even listed. Essentially what it was at first was
Ubuntu
______
Windows

then I made it

Windows
_____
Ubuntu

then I updated and now it's

Ubuntu
_____
Ubuntu

So I need to put a new list item in there to boot up XD

---

### Post by dpar on 2007-10-02
Can you post the output of


```
cat /boot/grub/menu.lst
```

---

### Post by nwkegan on 2007-10-02
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
# kopt=root=UUID=a8067f85-700d-4ceb-aa32-b1249a1ea838 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=a8067f85-700d-4ceb-aa32-b1249a1ea838 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=a8067f85-700d-4ceb-aa32-b1249a1ea838 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=a8067f85-700d-4ceb-aa32-b1249a1ea838 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=a8067f85-700d-4ceb-aa32-b1249a1ea838 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Ubuntu Kernels:
root

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=a8067f85-700d-4ceb-aa32-b1249a1ea838 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=a8067f85-700d-4ceb-aa32-b1249a1ea838 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=a8067f85-700d-4ceb-aa32-b1249a1ea838 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=a8067f85-700d-4ceb-aa32-b1249a1ea838 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

```

---

### Post by dpar on 2007-10-02
Thats a new one on me.......
I think you'll have to wait for a knowlegable guru to help you on this one.....sorry:confused:

---

### Post by nwkegan on 2007-10-02
Thanks, it's not urgent or anything but I'm getting anxious because I'm worried it's irreparable.

---

### Post by dpar on 2007-10-02
Just out of curiosity try


```
sudo fdisk -l
```

---

### Post by jordanmthomas on 2007-10-02
It's not irreparable, don't worry.  :)

What happened is you are supposed to put Windows beneath the DEBIAN MAGIC WHATEVER section so when it updates grub it doesn't get removed.

open up your /boot/grub/menu.lst
```
gksudo gedit /boot/grub/menu.lst
```
Replace it with this one (I have removed a few kernels to give you room)
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
# kopt=root=UUID=a8067f85-700d-4ceb-aa32-b1249a1ea838 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=a8067f85-700d-4ceb-aa32-b1249a1ea838 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=a8067f85-700d-4ceb-aa32-b1249a1ea838 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=a8067f85-700d-4ceb-aa32-b1249a1ea838 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=a8067f85-700d-4ceb-aa32-b1249a1ea838 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Ubuntu Kernels:
root

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=a8067f85-700d-4ceb-aa32-b1249a1ea838 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=a8067f85-700d-4ceb-aa32-b1249a1ea838 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

[COLOR="Red"]title Windows XP
rootnoverify (hd0,0)
chainloader +1
boot[/COLOR]

```

..assuming your Windows is on your first partition.
(You can put the red text anywhere in your list if you have a feel for what's going on)

---

### Post by nwkegan on 2007-10-02
You have my undying gratitude! Thank you.

---

