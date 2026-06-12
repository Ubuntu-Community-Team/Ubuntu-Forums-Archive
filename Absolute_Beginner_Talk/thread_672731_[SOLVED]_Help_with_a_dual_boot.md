---
title: "[SOLVED] Help with a dual boot"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Gambini on 2008-01-19
I really hope this is a simple problem that I have overlooked while searching, but here's the setup:

I installed Ubuntu on my computer, and later decided to put Windows on it. The only dual boot experience I have had is Windows first, so I'm not really sure what to do. I can't make grub come up. I've tried boot flags on all of the partitions (one at a time, of course) in hopes that it would work, but it didn't. The only one that did was Windows. I guess what I'm getting at is: How do I make it so that grub will boot rather than just Windows without grub?

Here are my partitions, just in case it helps:
sda1= Root ("/")
sda2= /home
sda3= Windows XP
sda4= swap

Thanks in advance!

---

### Post by autocrosser on 2008-01-19
Take a look at this HowTo:

[http://ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub)

---

### Post by akniss on 2008-01-19
Once Windows is installed, it writes over the MBR where grub was.  In order to get to dual-booting again, you'll need to restore grub.  You can do that with the LiveCD.

[LIST=1]
[*]Boot from the Ubuntu LiveCD
[*]Open a terminal in the Live session, and enter the following commands:
[*]```
grub
root (hd0,0)
setup (hd0)
exit
```
[*]shutdown, take the LiveCD out, and boot.
[/LIST]

Good luck!

---

### Post by Gambini on 2008-01-20
Thank you so much! It's about 90% good, but now I have one more problem; Windows doesn't show up. Is there some sort of file that I need to add it to?

EDIT: I found the file and put Windows in, but I always get error 13. Here is what my /boot/grub/menu.lst looks like:
```

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
# kopt=root=UUID=45029b4d-5b5c-4dbc-816d-1837ef8820ae ro

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=45029b4d-5b5c-4dbc-816d-1837ef8820ae ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=45029b4d-5b5c-4dbc-816d-1837ef8820ae ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Windows XP Pro
root		(hd0,0)
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST
```
And my fdisk -l (just in case it helps):
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7fc27fc2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2432    19535008+  83  Linux
/dev/sda2            2433        8511    48829567+  83  Linux
/dev/sda3            8512       21259   102398310    7  HPFS/NTFS
/dev/sda4   *       21260       21337      626535   82  Linux swap / Solaris

```

---

### Post by Racecarandy on 2008-01-20
Hello, and thanks for making it less difficult to make the switch.  
So i'm having the same issue as the rest:  i need to repair grub.  I wanted to make windows the default OS so my wife doesn't freak, but still be able to use Ubuntu.  I ran "fixmbr" with my windows CD and it certainly made windows the default, but completely ruined the ability to log in to ubuntu.  I just got ubuntu setup last night to my liking and don't wanna change again!  Anyways, i'm running the live CD right now but it doesn't recognize anything it seems.  I've tried both Grub install methods but either work.  I don't know what to do next.  Thanks.

---

### Post by Gambini on 2008-01-20
Well, nevermind, I got it. I needed to put in (hd0,2). Thanks again for your help! And racecarandy: I used the terminal on the gparted live CD and did exactly what akniss said; if you wanted to know what I did.

---

