---
title: "Problem after instalation"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by ekosz on 2007-06-04
I recently just installed ubuntu Feisty Fawn for my computer and it is working great!!  The only problem is that I can't go back to my windows :P . 

What I did:
I have 2 SATA hard drives installed on my system.  One of them held windows and the other was blank.  What I did to install Ubuntu was I took out the power of the windows hard drive (so I made sure I didn't write over it) and then proceed to install Ubuntu on the remaining HD.  During the installation I made it so that Ubuntu only partitioned over half the disc to I could later go back and turn the remaining space into a FAT32 data source for my Windows and Linux systems to share information.   I went through the rest of the installation process and didn't really know what to do with the grub loader so I kept it at its default settings.  Now that I'm done I turned off the system and repluged the Windows SATA HD back in.  I was hoping that when I would start my system the Grub loader would recognize that there is a second OS on my system now and prompt me on which one I wanted to load into.... well it didn't.  The computer booted strait back into Ubuntu.

So what should I do.  Should I modify GRUB in some way shape or fashion?

---

### Post by FleetAdmiral74 on 2007-06-04
Um, I am in no way an expert....but if you just installed, and don't have much data on yet, reinstalling with the xp drive powered ON would probably work. I know, its not really a great solution, but I think it would work. THis way on instlall, grub should see the other hd and it should work automatically. THere ARE ways to edit grub, but thats harder.

---

### Post by Moop on 2007-06-04
Check your bios settings to see which hdd you are booting from. If you change your bios settings to boot from the other hdd, it should boot into windows. 

I agree with FleetAdmiral74's suggestion. Ubuntu will see the windows hdd and configure grub to boot it. 

Good luck!

---

### Post by Marious on 2007-06-04
OK what the issue is, which I know because I did myself just like you, since I did not know what I was doing, now well I still dont know what Im doing but its not as bad :p:p . So here is what happen, since GRUB did not see your other hard drive because it was not there it did not write it into the generated Grub file so there for the system does not boot via Grub at first and will see Ubuntu as your primary Drive and will automatically boot to it. If you have not had much done in Ubuntu you can do a reinstall with the other hard drive plugged in so that it will be recognized this time and Grub will boot up and give you a choice after you do the entire installation,  I would recomend you just do the partition you where going to do for FAT32 with Gparted and ensure you use FAT32 it will allow you to do so during installation when you are creating your partitions. Now if you do a search for Grub normally in your /boot folder it will not really have anything, since again it was not involved during your install. The files you might want to look at are device map it should list your hard drives, and your menu list here is mine so you know what IM talking about take a look. I also have multiple SATA drives in my machine.In case you want to manually create this but you will have to go through and ensure that GRUB boots first and that is yet another series of steps that you must take, just do a search for GRUB and you will find something. Good luck on this, probably easier to reinstall.

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
# kopt=root=UUID=fb99f7ae-314f-49c7-acc8-e4c6fd589ea0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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
# defoptions=quiet splash noapic

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
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fb99f7ae-314f-49c7-acc8-e4c6fd589ea0 ro quiet splash noapic
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fb99f7ae-314f-49c7-acc8-e4c6fd589ea0 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=fb99f7ae-314f-49c7-acc8-e4c6fd589ea0 ro quiet splash noapic
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=fb99f7ae-314f-49c7-acc8-e4c6fd589ea0 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd2,0)
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

---

### Post by Dougie187 on 2007-06-04
Could you post your grub menu file (/boot/grub/menu.lst) with code brackets around it?

---

### Post by ekosz on 2007-06-05
Here's a copy of my menu.lst
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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a81479e8-62e2-4f9c-a779-1c7019f24591 ro

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
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a81479e8-62e2-4f9c-a779-1c7019f24591 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a81479e8-62e2-4f9c-a779-1c7019f24591 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a81479e8-62e2-4f9c-a779-1c7019f24591 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a81479e8-62e2-4f9c-a779-1c7019f24591 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```'

I really don't feel like reinstalling since I now installed beryl, VLC and a bunch of other useful programs, but I will if there is no easy way.  Also because I have two 250gb its hard to tell which HD has Windows installed on it, is there a way to change the name of a HD, so that I can tell the difference?

---

### Post by Dougie187 on 2007-06-08
Ok well try adding this into your menu.lst file.

```
title           Windows XP
root            (hd1,1)
savedefault
makeactive
chainloader     +1
```

---

### Post by Inxsible on 2007-06-08
> **Dougie187 said:**
> Ok well try adding this into your menu.lst file.
 
```
title           Windows XP
root            (hd1,1)
savedefault
makeactive
chainloader     +1
```
 
Make sure you DONT add it between the BEGIN AUTOMAGIC KERNEL and END AUTOMAGIC KERNEL lines, else your Windows entry will be wiped on the next grub update.
 
Add it AFTER END AUTOMAGIC KERNEL
 
You will also have to change the drive path (hd1,1) depending on where your Windows entry is?
post the output of this command ```
sudo fdisk -l
``` -l is lowercase L
 
That will help us decide what drive number and what partition number your Windows is on

---

### Post by Dougie187 on 2007-06-08
Tou'che.
I just understood his problem to be he has two disks with 1 partition each. But good call on the automatic kernel bit.

---

### Post by Inxsible on 2007-06-08
> **Dougie187 said:**
> Tou'che.
I just understood his problem to be he has two disks with 1 partition each. But good call on the automatic kernel bit.
But the OP never said that he had only one partition on his windows drive. Even if that were the case, he'd have to put in (hd1,0) because the grub's disk recognition is zero-based and 0 actually means the first partition, 1 = second partition and so on.

---

### Post by Dougie187 on 2007-06-08
Once again, you are correct. 8 times the posts = 8 times smarter i guess. :)

---

### Post by Inxsible on 2007-06-08
> **Dougie187 said:**
> Once again, you are correct. 8 times the posts = 8 times smarter i guess. :)
now that's Tou'che

I have been wrong before and had people who have just 1 post correcting me. Believe me, I am just as new to Linux as the next noob. 

Just because I troll the forums more, doesnt make me an expert..and I don't claim to be one !

I quoted you in my first post in this thread, only because what you suggested was correct and to add a bit more info. Call me lazy if you will, but I didnt wanna go to my menu.lst and see what my actual entry was and then post it and since you already had it there, it was no use adding mine there too.

---

### Post by Dougie187 on 2007-06-10
@ekosz:
Is this resolved?

---

