---
title: "multi-boot problem - Hackintosh / Ubuntu / Haiku"
date: 2010-01-22
forum: Apple Hardware Users
---

### Post by natgab on 2010-01-22
I have a question for other brave souls like me that think dual-booting is not enough. Problem is that most tutorials are for Windows plus other operating systems. I don't have Windows on any of my HDs.
[COLOR="Red"][B]
--Something I forgot to mention, but brought to my attention in another thread. In case anybody doesn't know, Haiku OS is a new open source version of Be OS. It is not Linux based though.[/B][/COLOR]


**[COLOR="Blue"]SEE below for solution[/COLOR]**

My PC, which has been running Ubuntu and Haiku on two separate hard drives has just become a Hackintosh.\\:D/ I installed OS X 10.6.2 on my 3rd HD.(all internal)  All Operating systems work, but never more than two at a time. :(

**[COLOR="Red"]--OS X is on an 80GB HD, 2 partition. Main OS X & test OS X. GUID (HFS+ journaled)[/COLOR]**

I had been using Ubuntu / Haiku dual boot fine, using GRUB to choose between them. Ubuntu HD set in BIOS as 1st boot.
[B][COLOR="Red"]
--When I installed just these two HDs, I had them as MBR (FAT32) before installing OSs. Finally realized they needed to be GUID (HFS+ non-journaled) so that OS X could work with them.[/COLOR][/B]

When I added Mac OS X, it added Chameleon bootloader, and I changed OS X HD to boot 1st in BIOS.  It works and give me the Chameleon screen, listing Haiku as a Linux drive, and boots to it fine. But it does not see my Ubuntu HD.

**[COLOR="Red"]--For some reason, Chameleon bootloader was seeing/booting to Haiku, even though it was still MBR.  This kept me from changing to GUID, untill it was the only variable left to change.[/COLOR]**

I then tried adding OS X to my GRUB list, but I don't know if I did it right. I was able to make it dual boot, but maybe I need more instructions to make it triple boot. 

[COLOR="Red"]**--This won't work in Legacy GRUB. Possibly GRUB2 or rEFI, if you have experience with those bootloaders.**[/COLOR]

At the moment I have to use BIOS to swap between Ubuntu/Haiku or OSX/Haiku. I would prefer to have all 3 on one bootloader.

**[COLOR="Red"]--Now that all 3 internal HDs have been GUID partition map, Chameleon can see the OS inside of each.  One important note, Haiku was able to go back on its own 10GB HD, GUID (Be partition).  But the only way I could get Ubuntu to boot was to partition the HD in two.  It would only boot if Ubuntu was the second partition with GRUB bootloader inside the partition in the 160GB HD. The first partition is FAT32, read/write any of the three Operating Systems.[/COLOR]**

[COLOR="Blue"]**NOTE: I am still getting an "initialize this HD ?" for the Haiku HD on OS X. No error in Ubuntu. Will update if I fix this problem.**[/COLOR]

Current GRUB below: 

[COLOR="Red"]**--Ubuntu now has a non-modified GRUB**[/COLOR]

```
Notes for GRUB errors:

jaleman@bebox:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-17-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.28-3-rt
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

__________________________________

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
default         0

### timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# kopt=root=UUID=fad67457-b54e-46e4-8540-613cce54dcdc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fad67457-b54e-46e4-8540-613cce54dcdc

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title           Ubuntu 9.04, kernel 2.6.28-17-generic
uuid            fad67457-b54e-46e4-8540-613cce54dcdc
kernel          /boot/vmlinuz-2.6.28-17-generic root=UUID=fad67457-b54e-46e4-8540-6$
initrd          /boot/initrd.img-2.6.28-17-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid            fad67457-b54e-46e4-8540-613cce54dcdc
kernel          /boot/vmlinuz-2.6.28-17-generic root=UUID=fad67457-b54e-46e4-8540-6$
initrd          /boot/initrd.img-2.6.28-17-generic

title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            fad67457-b54e-46e4-8540-613cce54dcdc
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=fad67457-b54e-46e4-8540-6$
initrd          /boot/initrd.img-2.6.28-11-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid            fad67457-b54e-46e4-8540-613cce54dcdc
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=fad67457-b54e-46e4-8540-6$
initrd          /boot/initrd.img-2.6.28-11-generic

title           Ubuntu 9.04, kernel 2.6.28-3-rt
uuid            fad67457-b54e-46e4-8540-613cce54dcdc
kernel          /boot/vmlinuz-2.6.28-3-rt root=UUID=fad67457-b54e-46e4-8540-613cce5$
initrd          /boot/initrd.img-2.6.28-3-rt
quiet

title           Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode)
uuid            fad67457-b54e-46e4-8540-613cce54dcdc
kernel          /boot/vmlinuz-2.6.28-3-rt root=UUID=fad67457-b54e-46e4-8540-613cce5$
initrd          /boot/initrd.img-2.6.28-3-rt

title           Ubuntu 9.04, memtest86+
uuid            fad67457-b54e-46e4-8540-613cce54dcdc
kernel          /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Haiku OS
rootnoverify    (hd2,0)
chainloader     +1

title		Lisa HD
rootnoverify	(hd1,0)
chainloader	+1

title		Test HD
rootnoverify	(hd1,1)
chainloader	+1

```

Please note that my Mac OS X HD is in two partitions of OS X. Since its a Hackintosh, I have a test partition to test updates before applying them to my main system.

**[COLOR="Red"]--OS X still in Main and test partitions[/COLOR]**

One last note, when I boot to OS X, it does not see my Ubuntu or Haiku HD. Do any of you Ubuntu/OS X dual booters have this problem?

[COLOR="Red"]**--Problem solved with switch to GUID, see above.**[/COLOR]

---

### Post by linuxopjemac on 2010-01-22
Google is your friend, search for triple boot Ubuntu hackintosh windows

here for example:
[http://liveinformant.com/software/triple-boot-osx-hackintosh-guide/](http://liveinformant.com/software/triple-boot-osx-hackintosh-guide/)

EDIT:
sorry for my fast replay, I thought windows...now I see Haiku

---

### Post by natgab on 2010-01-22
> **linuxopjemac said:**
> Google is your friend, search for triple boot Ubuntu hackintosh windows

here for example:
[http://liveinformant.com/software/triple-boot-osx-hackintosh-guide/](http://liveinformant.com/software/triple-boot-osx-hackintosh-guide/)

EDIT:
sorry for my fast replay, I thought windows...now I see Haiku

---Yeah, even in other Apple forums, its OS X / Windows. I did post to the Hackintosh forum too.  But most are also asking how to run Windows on their Hack, since it won't work with Boot Camp usually.

---

### Post by Ken147 on 2010-01-22
a word of caution..... don't run software update in 10.6.2, apple lately has been going after the Hackintoshes so they won't work, so I'd leave it at 10.6.2

---

### Post by natgab on 2010-01-23
> **Ken147 said:**
> a word of caution..... don't run software update in 10.6.2, apple lately has been going after the Hackintoshes so they won't work, so I'd leave it at 10.6.2

---Thanks.  I know they messed up the netbooks w/ Atom processors with 10.6.2.  That is why I made an extra test partition of OS X.

---

### Post by Nycthbris on 2010-02-09
Interesting setup. I've been wanting to try a triple boot for a while now, but I have a dilemma  maybe you could shed some light on:

If I have two HDs, one with Ubuntu and Windows using a dedicated /boot partition (with GRUB2), and a second HD with OSX on it, would it be possible to point GRUB2 to directly boot OSX on the second HD? Or would I need some kind of bootloader (Chameleon, rEFIt, etc.) on the OSX HD also? I'd rather not change the partitioning on the Ubuntu/Windows HD.

---

