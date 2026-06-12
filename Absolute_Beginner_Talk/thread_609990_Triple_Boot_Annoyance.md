---
title: "Triple Boot Annoyance"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by shamushand on 2007-11-11
I have a triple boot setup between XP, Vista, and Ubuntu. I just find it really annoying that first I have to go though GRUB, then into the Windows bootloader. The point is, I want all three in a single bootscreen.

My setup:

(Disk,Partition)
(0,0) Windows Vista
(0,1) Games
(1,0) Windows XP
(1,1) Ubuntu 7.04

I installed Vista first, then Windows XP, then Ubuntu last.

I can boot into Ubuntu and Vista using GRUB, I just need to add XP.
I've tried:

```
title  Windows XP
root  (1,0)
chainloader  +1
```

When I select it in GRUB though, I just get a blank screen, and the computer reboots itself.

So I tried:

```
title  Windows XP
map  (1,0)
map  (0,1)
root  (1,0)
chainloader  +1
```

Then I get a screen saying:

> Starting up...

NTLDR is missing, press Ctrl+Alt+Del to reboot

So what should I do? All help highly appreciated. :)

P.S.: menu.lst attached.

---

### Post by kshane on 2007-11-11
Sure seems convoluted...

Are you using two HDDs?

Your second code window for booting XP seems to contradict itself.

Kevin

---

### Post by shamushand on 2007-11-11
Then what should I put in there, exactly?

Here's a better description of my setup:

1st Hard drive (80GB)
 1st Partition: Windows Vista (55GB)
 2nd Partition: Games (25GB)

2nd Hard Drive (80GB)
 1st Partition: Windows XP (35 GB)
 2nd Partition: Ubuntu 7.04 (45GB)

So yes, I'm using two HDD's. :)

---

### Post by kshane on 2007-11-11
> **shamushand said:**
> Then what should I put in there, exactly?

Here's a better description of my setup:

1st Hard drive (80GB)
 1st Partition: Windows Vista (55GB)
 2nd Partition: Games (25GB)

2nd Hard Drive (80GB)
 1st Partition: Windows XP (35 GB)
 2nd Partition: Ubuntu 7.04 (45GB)

So yes, I'm using two HDD's. :)

Okay..  Not sure if this one will work for you or not, but it's more likely to than what you had.  I'm no Guru, but give it a try...
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
# kopt=root=UUID=fd5eb63f-1c5b-431b-92ca-c2c9e8b60468 ro

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

title		Ubuntu 7.04
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fd5eb63f-1c5b-431b-92ca-c2c9e8b60468 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu 7.04 (Recovery Mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fd5eb63f-1c5b-431b-92ca-c2c9e8b60468 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Microsoft Windows Vista/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Windows XP
root		(hd1,0)
savedefault
makeactive
chainloader	+1


### END DEBIAN AUTOMAGIC KERNELS LIST

```
Kevin

---

### Post by kshane on 2007-11-11
PS:  Your first entry in menu.lst will be the "default" boot.  So, whichever one you want to boot to automatically should be the first entry (top to bottom)...

Kevin

---

### Post by shamushand on 2007-11-11
Ok, I'll go ahead and try that then. :)

---

### Post by shamushand on 2007-11-11
I tried that, and I got:

> Starting up...

GRUB Error 11:
Cannot read data from disk

So I tried:

```
title		Windows XP
map (hd1) (hd0) 
map  (hd0) (hd1)
root  (hd1,0)
savedefault
makeactive
chainloader	+1
```

And got:

> Starting up...

NTLDR is missing, press Ctrl+Alt+Del to reboot

Any more suggestions? ](*,)

---

### Post by shamushand on 2007-11-11
Anyone? Come on, people vote on the poll 'Yes', but don't post help. :(

---

### Post by kshane on 2007-11-11
> **shamushand said:**
> I tried that, and I got:



So I tried:

```
title		Windows XP
map (hd1) (hd0) 
map  (hd0) (hd1)
root  (hd1,0)
savedefault
makeactive
chainloader	+1
```

And got:



Any more suggestions? ](*,)

I think the problem is that there needs to be something in the MBR for loading the WIndows XP.  It seems to not be there for some reason.  I would think maybe the best would be for XP and Vista to be on the same drive.  Just a guess though.  Sorry it didn't work for you.  I took care of that problem by Dumping all MS from my system.  Works great now!  I know that doesn't help... Sorry...  Repost your prob again and see of one of the "Gurus" will see and help...

Kevin

---

### Post by shamushand on 2007-11-11
It can't be XP, because I boots fine through Vista's bootloader.

---

### Post by gn2 on 2007-11-11
I believe there's a problem with the drives being re-numbered after the installation and Grub can't find them.

Have a read of this thread from this post onwards: [http://ubuntuforums.org/showpost.php?p=3503938&postcount=148](http://ubuntuforums.org/showpost.php?p=3503938&postcount=148)

---

### Post by rsambuca on 2007-11-11
It is possible to do, but not using grub.  The vista longhorn loader overtakes XP, so grub will never be able to access XP directly, unless you install Vista on a separate drive from XP, and remove the XP drive first.  There is a separate loader that will work called [easybcd]("http://neosmart.net/dl.php?id=1").

---

### Post by shamushand on 2007-11-11
> **rsambuca said:**
> It is possible to do, but not using grub.  The vista longhorn loader overtakes XP, so grub will never be able to access XP directly, unless you install Vista on a separate drive from XP, and remove the XP drive first.  There is a separate loader that will work called [easybcd]("http://neosmart.net/dl.php?id=1").

I use it, but GRUB is on top. I can't get Vista's bootloader to come first. :(

---

