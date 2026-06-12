---
title: "Lost my partition"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by jtb108 on 2007-06-03
Hello,

I installed Ubuntu several months ago and partitioned my hard drive to be half WIndows XP and half Ubuntu. The Windows option has now disappeared when I boot up.

The partition has been there under Edgy Eft and Feisty Fox but disappeared right after I did the laster Feisty upgrade yesterday.

I really like Ubuntu. It is so much better than Windows.  I use Ubuntu 90% of the time.

However, I must run several Windows program as part of my job.  These are special programs written especially for my job.  And now I can't access them on my computer.

I would appreciate any help.

Thank you,

John Boncheff

---

### Post by Inxsible on 2007-06-03
Did you perform a kernel update from -15 to -16 ?

Did you have the windows entry within the Automagic Kernel Entries in the grub menu.lst ?

If so, I am afraid the kernel update removed the entries.  Check your menu.lst
```
gksudo gedit /boot/grub/menu.lst
```

If you do not find windows entries in it, then read ahead........

You can log in to the recovery mode and change the menu.lst
WARNING : DO THE FOLLOWING AT YOUR OWN RISK (changing grub menus is always risky, but i do not think you have a choice)
```
sudo nano /boot/grub/menu.lst
```

Look for a line like this
```
### END DEBIAN AUTOMAGIC KERNELS LIST
```
Add these lines to it afte the above :
```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Of course, you will need to change the partition that it lies on. mine is on the first drive, first partition so i have (hd0,0)

---

### Post by jtb108 on 2007-06-03
Thank you for your response.  I am still pretty clueless about Ubuntu.

Here is what happens when I type in your commands.


When I type"gksudo gedit /boot/grub/menu.lst"

I first get this message:

(gedit:6090): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Then the following appears:  (as you can see, the Debian Automagic Kernals List does show the partition.  It just doesn't show up as an option when I boot up.



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
# kopt=root=UUID=bb2a5592-b8a9-4e09-a5cb-ffdc80fad267 ro

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
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=bb2a5592-b8a9-4e09-a5cb-ffdc80fad267 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=bb2a5592-b8a9-4e09-a5cb-ffdc80fad267 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=bb2a5592-b8a9-4e09-a5cb-ffdc80fad267 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-386
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=bb2a5592-b8a9-4e09-a5cb-ffdc80fad267 ro single
initrd		/boot/initrd.img-2.6.20-15-386

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=bb2a5592-b8a9-4e09-a5cb-ffdc80fad267 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=bb2a5592-b8a9-4e09-a5cb-ffdc80fad267 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=bb2a5592-b8a9-4e09-a5cb-ffdc80fad267 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=bb2a5592-b8a9-4e09-a5cb-ffdc80fad267 ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=bb2a5592-b8a9-4e09-a5cb-ffdc80fad267 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=bb2a5592-b8a9-4e09-a5cb-ffdc80fad267 ro single
initrd		/boot/initrd.img-2.6.17-10-generic

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
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1



Thank you,

John B.

---

### Post by Inxsible on 2007-06-03
Ok. you are in luck !!
Your XP is still there, the problem is pretty simple actually.

Because of multiple kernel updates, you have too many Ubuntu log ins, and therefore, windows scrolls down below the screen. 

You can either:
comment the old ubuntu kernel entries
OR
Put windows up top -- that will make Windows your default entry -- I would NOT go for this option because you have to be again careful that you dont put it between the automagic kernel ...to much hassle.

Simply comment - the older kernel entries for ubuntu.

or if you have stable latest kernels,  you can actually un-install the older kernels from the synaptic package manager. Post back if you want to do this.

---

### Post by Inxsible on 2007-06-03
> (gedit:6090): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Dont worry about this. Its a harmless bug and has already been reported

---

### Post by Inxsible on 2007-06-03
you can probably get rid of your -10 and -11 kernels as your -15 i assume is stable. You should always keep atleast one older kernel so that you can log into it, in case your newer kernel gives you problems

---

### Post by Inxsible on 2007-06-03
For example, I have only two kernel entries.
2.6.20-15 -generic and 2.6.20-16-generic

My newer one i.e. -16 is giving me a couple of problems like phantoms drive icons and such, so i keep using the -15 one instead until the -16 one gets fixed :)

---

### Post by jtb108 on 2007-06-03
Hello,

I went ahead and removed kernals -10 and -11 from my system. (So far no major crashes) and that has place Windows XP back on my login screen.

Thank you very much to everyone for helping me out.

John B.

---

### Post by Inxsible on 2007-06-03
> **jtb108 said:**
> Hello,

I went ahead and removed kernals -10 and -11 from my system. (So far no major crashes) and that has place Windows XP back on my login screen.

Thank you very much to everyone for helping me out.

John B.

Glad you got it sorted out !!

Cheers !

---

