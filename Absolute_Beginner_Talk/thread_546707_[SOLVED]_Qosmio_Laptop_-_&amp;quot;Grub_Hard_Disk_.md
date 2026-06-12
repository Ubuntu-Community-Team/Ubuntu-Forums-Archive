---
title: "[SOLVED] Qosmio Laptop - &amp;quot;Grub Hard Disk Error&amp;quot;"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by ncwilde43 on 2007-09-09
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=362326&amp;highlight=Grub+hard+disk+error](http://ubuntuforums.org/showthread.php?t=362326&amp;highlight=Grub+hard+disk+error) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm quite a noob myself but here is my problem.  I installed Feisty using the LiveCD and I get the following error when trying to boot: "Grub Hard Disk Error".  I am able to boot into Feisty using the LiveCD - "Boot from hard disk"

Here are my computer specifications: Toshiba Qosmio G15R,  Installed Feisty on 60 gig hd.  40 gig hd is full of photos, docs, music etc.  Windows is NOT installed.  60 gig is not partitioned (at least I think)

Here are the possible solutions that I've tried from previous posts:

-Bios Settings: hard drive 1, ( 60 gig is set to boot first)

-Reinstalled Feisty twice from scratch

-Reinstalled Grub using Super Grub

-Rinstalled Grub using:
```
sudo grub
root (hd0,0)
setup (hd0)
quit
```

-Updated Bios

Here is my output of fdisk -l
```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4864    39070048+   7  HPFS/NTFS

```

Here is also my device.map
```
(hd0)	/dev/sda
(hd1)	/dev/sdb
```

Also my menu.lst
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
# kopt=root=UUID=638a0730-c7fa-4d5c-8d14-dec8e418d5fe ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=638a0730-c7fa-4d5c-8d14-dec8e418d5fe ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=638a0730-c7fa-4d5c-8d14-dec8e418d5fe ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=638a0730-c7fa-4d5c-8d14-dec8e418d5fe ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=638a0730-c7fa-4d5c-8d14-dec8e418d5fe ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I've found that other people with Qosmio laptops are having the same problem problem

Has anyone found a solution for Feisty? If there is no solution I might try and install 6.06 and upgrade

thanks!

---

### Post by gn2 on 2007-09-09
I've read about a very similar problem before, try installing to the desired hard drive with the other hard drive physically removed.

Also, reading this may help: [http://ubuntuforums.org/showpost.php?p=3282917&postcount=9](http://ubuntuforums.org/showpost.php?p=3282917&postcount=9)

---

### Post by seanix on 2007-09-09
hello,
I too have a Qosmio laptop and the only distro that CAN install a boot loader is opensuse 10.2

Last night I had the wireless card working for the first time using a live cd but after permanent install, the nvidia driver could not be loaded (messed up the x server) and the wireless was again not working so envy couldn't fix it.

If someone has a fix for grub so that a qosmio laptop can be booted propper, I'd be happy to switch for good.

Let's hope some genius reads this :)

---

### Post by gn2 on 2007-09-09
The problem would seem to be that GRUB renames or reorders the drives during/after the installation.

It may be possible to circumvent this by the tried and tested method of removing the Windows hard drive and installing Ubuntu and GRUB to the second hard drive then using the "Boot Device Selection Menu" (normally F2 on Toshibas) to choose the Ubuntu/GRUB drive at boot time.
The default OS can be chosen by setting it's hard drive before the other hard drive in the BIOS boot order.

You don't have to use GRUB, you can use GAG or LILO bootloaders instead, more details in the Hermanzone link in my sig, which I would advise reading through thoroughly.

---

### Post by seanix on 2007-09-09
thank you gn2 :)
I should have mentioned that I no longer have a second hd in my laptop becasue is failed a few weeks ago.

So here's the situation:
only one hd (hd0)

only OS is linux mint 3.1

what are the commands to edit grub so that it would boot without having the CD present every time?

This information would be helpful for many people so hopefully some kind soul will play "terminal" ;) and help us newbies out :)

thanks!

---

### Post by ncwilde43 on 2007-09-10
Ok, I tried removing the second hard drive and then booting from the LiveCD.  When choosing "start and Install Ubuntu" It goes to the Ubuntu loading screen then gives me the following error:

/bin/sh: can't access tty; job control turned off
(initramfs) [ 34.084000] ata1: port failed to respond (30 secs, status 0xd0)

and then ends with a "(initramfs)" command prompt.  I am able to boot, however, using the "boot from disk" option when I only have one hard drive in (although it takes a lot longer).  Is there anything else I can try in order to reinstall ubuntu with only having 1 hard drive installed?

Oh yeah, I also get the "Grub Hard Disk Error" again when trying to boot from only 1 hard drive.

---

### Post by ncwilde43 on 2007-09-13
Solved it!  

Had to uninstall the QosmioPlayer that comes with Laptop.  QosmioPlayer is a program used to play DVD's, TV and Audio CD's without booting into the OS.  The computer comes with a QosmioPlayer Recover CD, so just pop it in, boot up using the CD and uninstall.  

Grub Hard Disk Error fixed!

Thanks to rooreleased from this post:[http://ubuntuforums.org/showthread.php?t=56160&highlight=qosmio+laptop](http://ubuntuforums.org/showthread.php?t=56160&highlight=qosmio+laptop)

---

