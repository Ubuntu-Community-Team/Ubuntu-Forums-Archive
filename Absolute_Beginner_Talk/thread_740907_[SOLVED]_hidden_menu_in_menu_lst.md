---
title: "[SOLVED] hidden menu in menu lst"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by marine63 on 2008-03-31
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

how do i make it so itll show the menu so i dont need to press esc
do i delete this part?

---

### Post by LowSky on 2008-03-31
comment out hidden menu

just add # before hiddenmenu

like so

#hiddenmenu

---

### Post by marine63 on 2008-03-31
it didnt work :(

---

### Post by rickocop on 2008-03-31
It's possible that "hiddenmenu" appears twice in the menu.lst file and is not commented out (doesn't have a '#' before it) at one point. 

open a terminal and try typing:

sudo cat -n /boot/grub/menu.lst | grep hiddenmenu

this should give you an output with every occurence of hiddenmenu and its line number

---

### Post by webaake on 2008-04-07
I have no grubmenu either and the command above gives only this:

sudo cat -n /boot/grub/menu.lst | grep hiddenmenu
    21  ## hiddenmenu
    23  ## hiddenmenu


A grub menu can be crucial when problems arise, for example when compilng your own kernels.

I've also tried changeing the timeout to 12, changeing the resolution and lots more, but to no avail.

How can I get my grub mneu back?

---

### Post by myusername on 2008-04-07
you should always make a backup of any system file you edit

---

### Post by chewearn on 2008-04-07
> **webaake said:**
> I have no grubmenu either and the command above gives only this:

sudo cat -n /boot/grub/menu.lst | grep hiddenmenu
    21  ## hiddenmenu
    23  ## hiddenmenu


A grub menu can be crucial when problems arise, for example when compilng your own kernels.

I've also tried changeing the timeout to 12, changeing the resolution and lots more, but to no avail.

How can I get my grub mneu back?


If you have multiple linux installations in your PC, you might be looking at the wrong menu.lst.

---

### Post by webaake on 2008-04-07
I have only one OS installed, on just one disk (hd 0,0), so everything boots OK but I can't use the grub menu.

---

### Post by forestpixie on 2008-04-07
You'll have to post the whole thing here - 
```
cat /boot/grub/menu.lst
```

---

### Post by webaake on 2008-04-07
OK. Here it is:

 sudo cat /boot/grub/menu.lst
Password:
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
timeout         12

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
##hiddenmenu
#color black/green black/white

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=4653cc47-c2cd-4837-be00-5a8cac896ecc ro

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
# defoptions=vga=769

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
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##
title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=4653cc47-c2cd-4837-be00-5a8cac896ecc ro vga=769
initrd          /boot/initrd.img-2.6.20-16-generic
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=4653cc47-c2cd-4837-be00-5a8cac896ecc ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=4653cc47-c2cd-4837-be00-5a8cac896ecc ro vga=769
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=4653cc47-c2cd-4837-be00-5a8cac896ecc ro single
initrd          /boot/initrd.img-2.6.20-15-generic
### END DEBIAN AUTOMAGIC KERNELS LIST

AND I have tried the solutions in this thread:

[http://ubuntuforums.org/showthread.php?t=454392&page=3](http://ubuntuforums.org/showthread.php?t=454392&page=3)
 
Still no go!

Thx for any help!

---

### Post by bonzodog on 2008-04-07
Try uncommenting the color line below the hidden menu option. I think it might need that.

---

### Post by webaake on 2008-04-08
I've tried that too and no luck.  I suspect there must be some problem with the framebuffer driver, vesafb, which I activated.

One solution would probably be to activate the nvidiafb driver, buit then the real nvidia driver would be useless. I'm useing compiz/awn and have a nvidia 7600 GS card, which is fairly new. I think this is the problem - with an older card I wouldn't have the problem with grub. 

And it can be that bug that they're talking about and the htread I mentioned above.

Maybe it'll be alright in Hardy?

---

