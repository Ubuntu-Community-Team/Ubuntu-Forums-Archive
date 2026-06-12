---
title: "install ubuntu over ubuntu = install 2 ubuntu ? can i remove one ?"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by kurniawands on 2006-08-03
guys,
that day when i was installing my first ubuntu, then after, xp, my os selector won't come up, so i decide to re-install ubuntu without reformating the partition.

now on the os selector, there are 2 ubuntu and 1 xp installed.

can i remove that other ubuntu ? and how to do it without messing the other one ? or should i reformat the whole ubuntu partition and start install it again from the begining ? (please don't say that...)](*,)

---

### Post by Sutekh on 2006-08-04
You may not need to completely re-install.  I just wonder if it's not just a case of a duplicate entry in the GRUB menu (OS selector).

If you load Ubuntu, can you then open the GRUB menu file and paste the contents here so we can have a look at it?

Open a Terminal window (Applications -> Accessories menu) and use this command to open the GRUB menu
```
gedit /boot/grub/menu.lst
```
Then paste the contents back here.

---

### Post by kurniawands on 2006-08-04
sorry, just see your message right now, yes... off course, but i'm not on my dapper right now, i'll do it after the office hour. i'll post it very soon. thanks before....:D

---

### Post by kurniawands on 2006-08-04
hi sutekh,
here it is...

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
# kopt=root=/dev/hda2 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by soonindallas on 2006-08-04
looking at your menu.lst you have one ubuntu installed and 2 different kernels:

kernel /boot/vmlinuz-2.6.15-26-386
and
kernel /boot/vmlinuz-2.6.15-23-386

This might have been after an automatic update, it's not a worry.

I suggest you keep the most recent one, you can delete the other if you wish.

I do automatic updates and I have 2 kernels on my system.  That way, if you do the update, reboot and for some reason there is a problem, you can still boot ubuntu using the previous kernel using grub (OS selector).  When a new kernel is offered, I accept the new one (sometimes it also involves new associated packages like whatever_version_restricted_modules) and I delete the oldest one.

You can delete the 2.6.15-23 kernel in synaptic:

System>Admin>Synaptic and enter your password

Search for linux-image and you will see the kernels you have installed with green boxes next to them. Today mine shows 2.6.15-26 and 2.6.15-25 installed.

Right-click in the one you want to remove and select "complete removal"

**!! DO NOT !!** remove the kernel you are currently running.  So if you want to remove X.X.XX-23 make sure you are running -26.  you can check this by typing ```
uname -r
``` in a terminal.  This command will return the current running kernel version.

Click on "apply" still in synaptic and the changes will be applied (you might have to click once again on OK).

The kernel will be removed from you disk and its grub entry will also be removed.

---

### Post by confused57 on 2006-08-04
Until Sutekh gets back, to me it looks like your 2nd Ubuntu installation just installed over top of the first one...your menu.lst just shows an old and newer kernel(which was probably installed during an update).
Also, you could check the output of:

```
sudo fdisk -l
```
The -l is a small "L"
This will show your partitions.

You may want to wait on Sutekh, he's quite experienced and knowledgable...but wanted to give you my 2 cents worth of opinion.

Edit:  Soonindallas beat me to it.

---

### Post by likeawalrus55 on 2006-08-04
I also have the same problem, but instead of having two seperate kernels due to updates, i have a desktop kernel and a server kernel.  How exactly do u get a server kernel, and should i be using it.  I am still new to ubuntu...

---

### Post by kurniawands on 2006-08-04
hehehehe... thanks guys... problem solved in no time !!!

that's what makes me like ubuntu. support is something you can get anytime, anywhere... and ppl are soooo friendly and helpful... wish i can be a contributor someday... :idea:

---

### Post by Sutekh on 2006-08-06
> **confused57 said:**
> 
You may want to wait on Sutekh, he's quite experienced and knowledgable...but wanted to give you my 2 cents worth of opinion.

Edit:  Soonindallas beat me to it.
These days you could be waiting for me for weeks! Don't know about knowledgable, but I have been using Ubuntu for a while now, and you tend to see similar issues coming up, especially those that you have wondered about yourself!

But you guys are both right, and that's what I love about these forums, there is always someone who is willing and able to help.

> **kurniawands said:**
> hehehehe... thanks guys... problem solved in no time !!!

that's what makes me like ubuntu. support is something you can get anytime, anywhere... and ppl are soooo friendly and helpful... wish i can be a contributor someday... :idea:
You may want to keep that kernel, unless you are running very low on space as they are only a couple of megs (image + initial ram disc) each. 

I'd suggest trying out the newer kernel from the update for a while and make sure that you have the same performance that you had on the older kernel. Hopefully it will be better! I have found, on one occasion only though, that it was better for me to keep using an old kernel until an even newer one was released.

But don't sweat it if you've already removed the older kernel.

 > **likeawalrus55 said:**
> I also have the same problem, but instead of having two seperate kernels due to updates, i have a desktop kernel and a server kernel. How exactly do u get a server kernel, and should i be using it. I am still new to ubuntu...
So you are new to Ubuntu, do you recall how you installed it? Was it using the Desktop CD (the LiveCD session)? Or did you install it using the Alternate CD (the text install)? Could you have accidently done a server install? I can't think of a reason why you would have both.

If you are using Ubuntu as an ordinary day to day OS on your computer, then there isn't a need for the server kernel.  

Does Ubuntu run to your liking using the desktop kernel?  If so, just remove the server kernel, using the instructions that **soonindallas** posted, taking care that you remove the correct one.

---

