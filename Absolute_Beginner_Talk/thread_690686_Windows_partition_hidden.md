---
title: "Windows partition hidden"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by Oneofchaos on 2008-02-07
I have a dual boot and somehow (think upon updating) hid my XP partition so that I can't boot up to XP anymore.  Only linux ubuntu I can boot up to.  Can anyone tell me the steps to take to recover it?

---

### Post by spiderbatdad on 2008-02-07
if you overwrote it, I believe it is lost. Look in /boot/grub/menu.lst to see if it is ## commented out for some strange reason.

---

### Post by Oneofchaos on 2008-02-07
I don't think I overwrote it.  I don't know what I did but a friend fixed it last time.  He can't help me now, and I don't know much about Ubuntu at all.

---

### Post by jan quark on 2008-02-07
run in linux this command

```
sudo fdisk -l
```

do you see your windows partition ?

probably ntfs or fat32 format

---

### Post by RxRated on 2008-02-07
never mind.

---

### Post by Oneofchaos on 2008-02-07
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dd071

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48631   390628476    7  HPFS/NTFS
/dev/sda2           48632       60300    93731242+  83  Linux
/dev/sda3           60301       60801     4024282+   5  Extended
/dev/sda5           60301       60801     4024251   82  Linux swap / Solaris

That's what I found

---

### Post by jordanmthomas on 2008-02-07
Alright then, first open a terminal
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```
```
gksudo gedit /boot/grub/menu.lst
```
and add this at the bottom:
```
title Windows
rootnoverify (hd0,0)
chainloader +1
boot

```
Save and close, and windows should now be in your list.  

It may also not be showing up because you have tons of kernels installed.  If that's the case, comment some of them out in your menu.lst while you're editing it.  The older kernels will be towards the bottom.

---

### Post by jw5801 on 2008-02-07
Take a look at /boot/grub/menu.lst:
```
gksu gedit /boot/grub/menu.lst
```
and see if your Windows partition still has it's entry right at the bottom. If it is there, try and find this section and make sure you're not only showing the first couple of options:
```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all
```

If your Windows partition is no longer mentioned then we can add it again, it should look something like this:
```
title           Windows
root            (hd0,0)
makeactive
chainloader     +1
```

---

### Post by Oneofchaos on 2008-02-07
Hey thanks I'll try that.  Also what the best way to learn linux if I want to read a little bit a night but I'll be by myself?  Just a lil something i want to learn.  Any book in particular to get, I was planning on getting one since I prefer paper over text.

---

### Post by jordanmthomas on 2008-02-07
In my experience, the best way to learn about Linux is to just use it.  
Eventually, you'll want to do something and not know how;  look it up, and poof!  You've learned something.

Many people have books they suggest, so I'll leave that to them.

---

### Post by Oneofchaos on 2008-02-07
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
timeout		5

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
# kopt=root=UUID=8aa49608-ea96-42b1-904a-930c13948b3e ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8aa49608-ea96-42b1-904a-930c13948b3e ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8aa49608-ea96-42b1-904a-930c13948b3e ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.22-12-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=8aa49608-ea96-42b1-904a-930c13948b3e ro quiet splash
initrd		/boot/initrd.img-2.6.22-12-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-12-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=8aa49608-ea96-42b1-904a-930c13948b3e ro single
initrd		/boot/initrd.img-2.6.22-12-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
title Windows
rootnoverify (hd0,0)
chainloader +1
boot

Is this what I'm supposed to see?

---

### Post by chick penguin on 2008-02-07
> **jordanmthomas said:**
> In my experience, the best way to learn about Linux is to just use it.  
Eventually, you'll want to do something and not know how;  look it up, and poof!  You've learned something.

Many people have books they suggest, so I'll leave that to them.

I am finding this a useful learning tool.
Book that may prove useful might we worth a look
 
Ubuntu Linux Toolbox   by Christopher Negus and Francois Caen

---

### Post by Oneofchaos on 2008-02-07
I can't seem to fix the problem

---

### Post by jw5801 on 2008-02-07
Try putting "makeactive" with it as well. That should fool Windows into thinking it's bootloader is the only one around :p

EDIT:
My entry looks like this, and works perfectly!
```
title           Windows
root            (hd0,0)
makeactive
chainloader     +1
```

---

### Post by Oneofchaos on 2008-02-07
Where exactly am I pasting it in tho?

---

### Post by Oneofchaos on 2008-02-07
Ok well it worked but now it boots up to linux, can I change the order it boots up into that way windows is at the top and automatically selected as the default?

---

### Post by jordanmthomas on 2008-02-07
Yes, move the Windows section in your menu.lst
(this)
```
title Windows
rootnoverify (hd0,0)
chainloader +1
boot
```

To **just above** the line that says
```
### BEGIN AUTOMAGIC KERNELS LIST
```
Now, Windows will be listed first and will be selected by default.

---

### Post by Oneofchaos on 2008-02-08
It didn't work...:(

---

### Post by jw5801 on 2008-02-08
So what happened instead?

---

