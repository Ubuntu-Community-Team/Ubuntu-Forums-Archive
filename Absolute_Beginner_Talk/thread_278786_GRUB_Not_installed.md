---
title: "GRUB Not installed?"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by t3ddyg on 2006-10-16
I installed Ubuntu 6.06 successfully off the Live/Install DVD.  After rebooting, GRUB doesn't load - my computer just launches straight into Windows XP.  I have 4 HD's.  Drive C and D are on my onboard mobo ide controller.  Drive E and F are on a pci ide controller.  Drive C contains my windows install.  I used partition magic to seperate drive D into two partitions, 1 with my windows stuff, and half the drive as unpartitioned space.  I then allowed the Ubuntu installer to format/partition the largest contiguous free space - which was the space I created on D.  Everything went well, but Grub doesn't load.  I don't know what is going on.  I took a screenshot of partition magic, to help demonstrate my drive map.

[[IMG]http://img92.imageshack.us/img92/5356/driveconfigah4.th.png[/IMG]](http://img92.imageshack.us/my.php?image=driveconfigah4.png)

---

### Post by confused57 on 2006-10-16
You could try booting up with the desktop live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
The -l is a small "L".

This should show how Linux recognizes your drives.

---

### Post by t3ddyg on 2006-10-17
Ok, I did just that.  Here are the results - 
[[IMG]http://img209.imageshack.us/img209/1314/fdiskqq1.th.png[/IMG]](http://img209.imageshack.us/my.php?image=fdiskqq1.png)

---

### Post by t3ddyg on 2006-10-17
I just noticed... it seems that my drive listing is out of order.  My onboard mobo ide controller drives are being listed as hde(C Drive)/hdf(D Drive).  My pci ide controller drives are listed as hda (E drive)/hdb (F Drive).

---

### Post by confused57 on 2006-10-17
I'm not sure if I can help you, but we need to see how grub recognizes your hard drives
Boot up with your live cd & mount the Ubuntu Linux partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

Once you're able to mount Ubuntu, post the output of the following files:

/boot/grub/menu.lst
(menu.lst is short for menu.list)

and

/boot/grub/device.map

Before you do the above, can you change the boot order in bios to boot first to your D drive(hdf)?  If Ubuntu boots, you can get the above information from your installation and maybe we can decide what to add to your grub to boot Windows(or add grub to your Windows mbr, if you're comfortable with that...I'd advise not to if at all possible).

---

### Post by t3ddyg on 2006-10-18
Ok, I tried changing the boot order.  For some reason it errored saying operating system not found.  Anyways - i mounted from the live cd, and got the information you wanted:

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
# kopt=root=/dev/hdf2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,1)

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

title		Ubuntu, kernel 2.6.15-23-386
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdf2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdf2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd3,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hde1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


```

```
device.map:
(hd0)	/dev/hda
(hd1)	/dev/hdb
(hd2)	/dev/hde
(hd3)	/dev/hdf

```

---

### Post by gn2 on 2006-10-18
Can you access a "Boot Device Selection Menu" at boot by pressing F8, or whatever key depending on make?

If you can, then bring up this menu and select the Ubuntu drive, and it should boot.

This thread may be worth reading: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by t3ddyg on 2006-10-19
I tried F8 - it didn't do anything...
I check the bios, and there was nothing in there along those lines, atleast not that I could see.  I have an Asus A7N8X-E Deluxe motherboard.

---

### Post by confused57 on 2006-10-19
You could try reinstalling grub(to hd3?), using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Basically, you'll boot up the live cd, open a terminal, enter:

```
sudo grub
```
this will give you a grub prompt, then enter:

```
find /boot/grub/stage1
```
this will probably show root (hd3,1)

```
root (hd3,1)
```
press enter, then enter
```
setup (hd3)
```

This should install grub to your "D" drive(hdf), then booting first to this drive should show the grub menu & boot Ubuntu...hopefully.  The thing I'm concerned about is that booting first to this drive may change the way grub recognizes your hard drives, i.e. the hd3 drive may be recognized as hd0, which would require root (hd0,1) to boot Ubuntu...I don't know for sure.  I wish I could give you a concrete answer that would definitely work, I'm just not familiar with your configuration.

I don't know, but it's possible that grub was installed to hda(E), can you boot first to your E drive?

It's your decision to try my suggestions, if you'd rather wait until someone more knowledgable(Herman, for one) sees your post.
I wanted to give you my thoughts on what was going on with your system.

---

### Post by t3ddyg on 2006-10-19
First off - I got it working.  It seems that there was some conflict with ubuntu install and my pci ide card.  I removed the drives connected to the pci ide card, flattened/reinstalled, and everything was just peachy - grub and all.  I then reconnected the drives to the pci ide card, and it is fine.  The funny thing is that the ubuntu installer STILL identified the primary master/slave hard drives connected to my mobo as hde/hdf?  I think it is because i just unplugged the ide cable to the pci card, not completely removed the pci card.  Either way - it is working now.  Thanks a lot for your dedication to helping me out.  I know these things are a pain, and it is very generous of all of you to donate your time like this.  Thankyou.

---

