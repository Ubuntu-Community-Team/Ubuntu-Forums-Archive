---
title: "Dual Booting XP and Ubuntu. Please Help."
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by m60dude5 on 2008-03-23
Hi. I just recently downloaded and installed Ubuntu on my computer. I am completely new to this, but followed some directions from the internet. This is my current situation.
I have a 160 GB drive, formatted into three 50 GB partitions. On one partition, Windows XP is installed (before Ubuntu).
I have another Hard drive, completely separate, which is 10 GB. The other partitions I have as extra space. So I have:
160 GB Drive: (Primary)
>>>of which 50 GB Windows XP
>>>of which 50 GB BLANK
>>>of which 50 GB BLANK

10 GB Drive (Slave)
>>>of which 10 GB Ubuntu

I installed Ubuntu using the bootable ISO. I put it on the blank 10 GB drive. I didn't touch anything on the Windows drive. Ubuntu set up nicely, and it boots fine. However, I am unable to access Windows XP in any way. I can't see it in the GRUB boot manager, and removing the 10 GB drive which Ubuntu was on completely from the system just causes a boot error. I would like to get my XP back, but still keep Ubuntu as well. I had a bunch of files on there. When I look in the disc manager in Ubuntu, I can see my Windows OS on the drive, it just won't show it to me on bootup. Is there some way I can add the XP option to the GRUB manager without reinstalling Windows, which would be a great pain. If there is, I need step by step directions since I am completely new to this.
Thanks for any help.

---

### Post by TeoBigusGeekus on 2008-03-23
I think you should go to BIOS and set as first boot device the hard disk on which xp is installed. 
Try it and post.

---

### Post by m60dude5 on 2008-03-23
Thanks for the post. I did that, set the drive that XP is on as the Primary and the other as the slave. However it still doesn't show XP at all. I want to see XP on the GRUB manager.

---

### Post by TeoBigusGeekus on 2008-03-23
Ok, type in a terminal
```
sudo fdisk -l
```
and post results.

---

### Post by m60dude5 on 2008-03-23
Ok, I typed "sudo fdisk -1" into the terminal and it says:

fdisk: invalid option --1
Usage: and then it lists all the uses:
fdisk [-b SSZ] etc.

Here, DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda
-u give start and end in sector units
-b 2048: for certain MO disks use 2048 byte sector

thats it. I'm not sure why it isn't working, i typed it in the exact way, multiple times.

---

### Post by TeoBigusGeekus on 2008-03-23
Mea culpa!

It's sudo fdisk -l

(THAT'S L NOT 1)

---

### Post by m60dude5 on 2008-03-23
I typed "l" not "1" and it says: ( i took a pic, i'm working off a laptop right now)
[IMG]http://bsa151.org/store/IMG_0098.jpg[/IMG]

Thanks.

---

### Post by TeoBigusGeekus on 2008-03-23
Now type in a terminal 
```
sudo gedit /boot/grub/menu.lst
```
Don't take a picture :) just copy and paste everything in that file in your post.

---

### Post by m60dude5 on 2008-03-23
I have to take pics because I haven't setup network connections on it yet and I am working on my laptop in the forum, and my ubuntu on my desktop. Sorry but I can't copy and paste.

Ok. Now.
 it opened a blank page with a tab that says menu.1st. What should I type?

---

### Post by TeoBigusGeekus on 2008-03-23
And again ...menu.lst that's .LST
(I' m sorry)

---

### Post by m60dude5 on 2008-03-23
Thats ok. It's my fault. I fixed that, now what should I type in the box.

---

### Post by m60dude5 on 2008-03-23
ok. now i see it. there is no way I can type that here, but I guess it is the same as everyone else's since I haven't edited anything. How do I add xp to the boot list from here? Thanks again for your patience, I am very new to this.

---

### Post by TeoBigusGeekus on 2008-03-23
Well first of all the file menu.lst shouldn't be blank. It stores information about the menu of grub loader.
The output of fdisk -l for me is
```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3a8a3a89

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa1d42923

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36482   293041633+   7  HPFS/NTFS
/dev/sdb2           36483       36483        8032+   f  W95 Ext'd (LBA)
teo@teo-desktop:~$ 

```
and my menu.lst file is as follows
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
# kopt=root=UUID=8a836653-f20c-4a3a-87a5-dddf010fce7b ro

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8a836653-f20c-4a3a-87a5-dddf010fce7b ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8a836653-f20c-4a3a-87a5-dddf010fce7b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

As you can see, at the end of the file I only have 3 options to choose cause I only have ubuntu on my primary partition (hd0).
What you should do, is add something like
```
title     Windows NT/2000/XP (loader)
root          (hd0,0)
makeactive
chainloader   +1
```
along with the other titles in order to be able to load window$.
If ubuntu loads on hd1,0 then I assume that xp is situated on hd0,0

---

### Post by m60dude5 on 2008-03-23
I'm sorry. No it's not blank. When I typed 1 it was, but after I changed that to l, my output looked the same as yours. I'll try adding (hd,0) on the end of the list and try again. Thanks for helping me out, I really appreciate it.

---

### Post by TeoBigusGeekus on 2008-03-23
Copy my code verbatim in order not to make a mistake (not hd,0 but hd0,0)
EDIT
If I wanted to do the same, say to add a windows partition I had on my second hd, the end of my menu.lst would be

```
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8a836653-f20c-4a3a-87a5-dddf010fce7b ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8a836653-f20c-4a3a-87a5-dddf010fce7b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title     Windows NT/2000/XP (loader)
root          (hd1,0)
makeactive
chainloader   +1

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by m60dude5 on 2008-03-23
Thanks so much for your help. I did exactly what you said and both XP and Ubuntu work great! Thanks alot, I really appreciate it.

---

