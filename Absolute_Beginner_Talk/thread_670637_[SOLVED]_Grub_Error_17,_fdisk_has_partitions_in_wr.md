---
title: "[SOLVED] Grub Error 17, fdisk has partitions in wrong order"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by VeganGeekChick on 2008-01-17
Hi.
I'm a long time geek (mostly into gadgets; not OS software), and a very short time Ubuntu user and multi-booter.

I have a problem.
I've got 4 partitions on my only hard drive (3 for operating systems and one for file storage), and they were all happy and working flawlessly until I installed the third OS.

Vista came preloaded on my laptop (Gateway C-140XL). It's at the beginning of my hard drive.
Then I installed Ubuntu 7.10 on a second partition. The dual-booting worked fine with Grub for about a month and a half.
Very recently, I wanted to try out OSx86 on a third partition for development and educational purposes, and it seemed fine until I rebooted after patching the OS. (Grub was working fine before the patch.)
After the OSx86 patch, Grub showed an Error 17.
I booted into Ubuntu from the LiveCD, and changed menu.lst to include OSx86.
I rebooted and still got Error 17.
So I went back into the Ubuntu LiveCD and took OSx86 back out of menu.lst.

I rebooted and still got error 17. And that's where I stand now.
My computer is pretty much useless now without booting from a CD.
Grub is my main bootloader, and I can't boot anything without it.

I have browsed the internet from my Ubuntu LiveCD for two days and haven't found anything that has worked.

My menu.lst file looks like this at the moment:
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
# kopt=root=UUID=ccc61ad5-c25b-43a2-97f3-ddb9f3bd939f ro

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ccc61ad5-c25b-43a2-97f3-ddb9f3bd939f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ccc61ad5-c25b-43a2-97f3-ddb9f3bd939f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
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
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

When I did fdisk -l, I got this:
```
root@ubuntu:~# fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc852d2ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sda2            5223        7833    20972857+  93  Amoeba
/dev/sda3            7834       10444    20971520   83  Linux
/dev/sda4           10444       14594    33329152    5  Extended
/dev/sda5           10444       14594    33328128    b  W95 FAT32

```
My partitions are in the wrong order. Linux should be second.
How do I fix this problem?
GParted sees the partitions in the correct order. (Vista, Ubuntu, Mac, Storage)
I don't know what to do.
And what is Amoeba? That's where OSx86 is, but shouldn't it come up as Mac OS or HFS+ or something??

I'm very confused and frustrated because I don't have very much experience with Linux or Mac systems or the Grub bootloader.

Any help will be greatly appreciated.

---

### Post by dcstar on 2008-01-17
> **VeganGeekChick said:**
> Hi.
I'm a long time geek (mostly into gadgets; not OS software), and a very short time Ubuntu user and multi-booter.

I have a problem.
I've got 4 partitions on my only hard drive (3 for operating systems and one for file storage), and they were all happy and working flawlessly until I installed the third OS.
........
I'm very confused and frustrated because I don't have very much experience with Linux or Mac systems or the Grub bootloader.

Any help will be greatly appreciated.

Edit all the (hd0,1) entries in the menu.lst file (including the default setting) to (hd0,2) and see what happens.

---

### Post by VeganGeekChick on 2008-01-17
I just tried it and it's not working.
I still get an error 17.
Thanks, though.

edited to add:
I think I know what the problem is; I just don't know how to fix it.
I think it's a conflict with what "fdisk -l" says and what the partition order really is.

My partitions are in this order:
Vista (boot), Ubuntu, OSx86, Storage
That's the order I made them in, and that's how it shows up in GParted.

Doing the fdisk thing showed them in this order:
Vista (boot), OSx86 (Amoeba??), Ubuntu, Storage

Is there a way to fix the partition order that fdisk shows?
I'm not sure this is why GRUB shows error 17, but it does look like a problem.

UPDATE:
I tried using the Super Grub CD I've heard a lot about, and I can successfully use it to boot into Vista (I'm actually typing this post from Vista, as opposed to the Ubuntu LiveCD earlier), but I can't boot into Ubuntu with it. (And I never even got far enough with OSX to boot it after installing it because that's when all these problems started.)

I looked at my partitions on Super Grub and it's also got my Ubuntu and OSX partitions switched from the original order.
After booting into Vista, I looked at Vista's disk management, and it makes no distinction between those two partitions. There's really no way of telling which one is which. They're both 20GB partitions.
Vista sees both of them as healthy, primary 20GB partitions with no used space or known formatting, despite both of them having some OS stuff and apps in there.

I know there's got to be some way to fix this mix-up.
Oh, and the only partitions with drive letters are my Vista partition, C:, and my Storage/"Stuff" partition, S:
Maybe that has something to do with it...??

---

### Post by VeganGeekChick on 2008-01-19
Alright. I've found the solution to the problem!
My partitions weren't switched or anything like that.
They were simply lying.
The Ubuntu partition said it was Amoeba, and the Mac OSX partition said it was Linux.
So, I followed [this website's instructions]("http://www.3till7.net/2007/10/25/grub-error-17/"), and it worked!

Basically, for those of you with the same type of problem, I went into fdisk and changed the hex codes for those two partitions (I had to do a bit of research to get an HFS+ code.)
I changed Ubuntu from 93 to 83 and restarted my computer, and Grub started right up without a problem! Now I can boot into whatever I want with no problem!

Thanks, dcstar, for the suggestion you gave. It didn't work for the type of problem I had, but thanks anyway. :) I appreciate the help.

---

