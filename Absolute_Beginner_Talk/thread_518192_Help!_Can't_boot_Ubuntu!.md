---
title: "Help! Can't boot Ubuntu!"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by alex-desktop79 on 2007-08-05
[Edit]: Read on for updates on the problem.
I edited my partitions and now grub wont find my Ubuntu partition (Error 22)

Here is a screenshot from partitionmagic:
[img]http://img399.imageshack.us/img399/4287/untitledph3.png[/img]

Editing grub should not be a problem, but what do I need to change?
I'm guessing the (hda0,1) stuff, logically I think that should be it...

Here is my menu.lst, from grub:
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
# kopt=root=UUID=5c56a6b6-4695-4899-aba8-f0866e469a86 ro

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5c56a6b6-4695-4899-aba8-f0866e469a86 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5c56a6b6-4695-4899-aba8-f0866e469a86 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5c56a6b6-4695-4899-aba8-f0866e469a86 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5c56a6b6-4695-4899-aba8-f0866e469a86 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,4)
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


```

This all boils down to a very simple change, I'm sure.

---

### Post by alex-desktop79 on 2007-08-05
bump

---

### Post by M_the_C on 2007-08-05
GRUB hard disk labelling works differently to Linux.  You got the first number right, but the second number also starts at 0. 
(hd0,0) would be your windows partition.

I can't remember if Extended partitions count as a number but they probably do.

Whoops, can't even follow my own advice.

---

### Post by ron999 on 2007-08-05
Hi
Yes, I think that you need to edit that boot menu list.
In four places it says
root    (hd0,4)

I think that you should change them to read
root    (hd0,1)

So you need to type into monitor
**sudo nautilus**
then find that file.
Look in boot folder
then in grub folder
the file name is menu.lst
Edit it and re-save it and reboot.

---

### Post by ron999 on 2007-08-05
ps
It's five places, don't forget the memtest86.

---

### Post by alex-desktop79 on 2007-08-05
From hd0,1 and hd0,2 (I thought maybe hd0,1 was the extended partition.)
I get an Error 17: Can't mount selected partition.

edit: On another note, I don't know if this changes anything but i resized my ext3 partition (~512mb bigger)

---

### Post by ccalvinfowler@aol.com on 2007-08-05
A. how many hard drives do you have

B. does install complete successfully

---

### Post by alex-desktop79 on 2007-08-05
A. One
B. ...what install? I have crucial files on that partition (I also know it's not corrupted, I can access it fine from windows)

---

### Post by ron999 on 2007-08-05
Please will you copy and paste into monitor
**ls -l /dev/disk/by-uuid**

---

### Post by alex-desktop79 on 2007-08-05
All right, let me boot the live cd.

---

### Post by alex-desktop79 on 2007-08-05
```
ubuntu@ubuntu:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2007-08-05 16:43 0f0838cf-e51d-468c-ac77-4cda10ad65b6 -> ../../sda3
lrwxrwxrwx 1 root root 10 2007-08-05 16:43 5c56a6b6-4695-4899-aba8-f0866e469a86 -> ../../sda5
lrwxrwxrwx 1 root root 10 2007-08-05 16:43 98580E6D580E4B08 -> ../../sda1
```

---

### Post by ron999 on 2007-08-05
Well, I was wondering whether that UUID number was correct for the location of the linux partition. But UUID=5c56a6b6-4695-4899-aba8-f0866e469a86
is the same in the printout that you've just posted, the same as the UUID number of the kernel in your earlier post.
So I'm out of my depth now.
Maybe someone else can help.

---

### Post by alex-desktop79 on 2007-08-06
bump, please help

---

