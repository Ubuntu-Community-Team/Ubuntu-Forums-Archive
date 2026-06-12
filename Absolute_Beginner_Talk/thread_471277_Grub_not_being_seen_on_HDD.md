---
title: "Grub not being seen on HDD?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by BHelts on 2007-06-11
Hello,
I have a fresh install of Feisty from the alternate install cd, and when I try to boot grub does not do its thing.  The hard drive is set as the second option behind the CDRom.  When I boot into the Alt Install disk I can select "Boot from first hard disk" and it works fine.  I'm sure there is something I'm missing in /boot/grub/menu.lst but I don't know enough about it to fix it myself.  Any help would sure be appreciated.  Thanks.

---

### Post by Pragmatist on 2007-06-12
Please post /boot/grub/menu.lst

---

### Post by southernman on 2007-06-12
Please - post the info from your menu.lst here.

Did you try and reinstall grub, just for sh*ts and giggles? ;)

---

### Post by BHelts on 2007-06-12
Sorry, just got back into work.  here's menu.lst
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
# kopt=root=UUID=e0c4f4bb-d1a4-410c-bf28-74947f951d59 ro

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
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e0c4f4bb-d1a4-410c-bf28-74947f951d59 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e0c4f4bb-d1a4-410c-bf28-74947f951d59 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e0c4f4bb-d1a4-410c-bf28-74947f951d59 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e0c4f4bb-d1a4-410c-bf28-74947f951d59 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by dstew on 2007-06-12
The menu.lst file seems OK. What is the exact error you get when you try to boot? That is, do you get any message out of grub? Maybe grub is not installed, and you are only getting a BIOS error that the disk is not bootable. If it is this problem then we need to install grub. That is easy to do.

If you only have the one hard disk, then you can re-install grub. Boot the Live CD, and go to a terminal window. Start grub by typing **grub**. That gets you the grub prompt **grub>**. At the grub prompt, type ```
find /boot/grub/menu.lst
```That should return the partition name of your Linux install, in the language grub understands. It might be (hd0,0). Whatever the answer, use it in the next grub command```
root (hd0,0)
```That tells grub where to go to get its menu.lst and other things. Finally, to install the grub boot loader into the master boot record of the first hard drive, enter```
setup (hd0)
```Note that it is not setup (hd0,0), but only (hd0). After that, quit grub (enter **quit**), take out the disk and reboot. It should work after that.

---

### Post by BHelts on 2007-06-12
Hey thanks for the help.
I am not getting any error messages on boot.  My BIOS boot order is CDRom, HDD, USB, LAN.  Well when I try to boot, it goes to trying to boot from the LAN.  When I boot to CD however and choose boot from first hard drive, i get Grub loading and everything works as planned.  I think that maybe I don't have a boot flag on the drive?  I don't know if that makes sense, but it's what i'm thinking.  I just still don't know enough about how to fix it.

---

### Post by Pragmatist on 2007-06-12
> **BHelts said:**
> I think that maybe I don't have a boot flag on the drive?

That is easy enough to check:
```
sudo fdisk /dev/hda
```

You can press "m" for help and you'll find that pressing "a" lets you select a partition.  If you want /dev/hda1, for example, you press "1".  Then there will be an asterik (*) next to the partition when you look at the partition table (which you can do by pressing "p").  When your all done you press "w" to write the changes.  HOWEVER, for some reason I don't have any partition with a boot flag set and my system works fine!  So, try this experiment at your own risk!

One minor point, for testing purposes, you might want to comment out the lines that say "hiddenmenu" and "timeout 3".  This will give you more time to choose from the grub list (or at least see if it is there!).  Also, you might want to choose a different kernel.

---

### Post by dstew on 2007-06-12
I think it's possible that your BIOS wants to see a boot flag on the drive. Anyway, it seems that the problem is between your BIOS and the disk for some reason. Have you tried putting the HDD first on the boot order list?

---

### Post by Inxsible on 2007-06-12
The problem is that you have hiddenmenu enabled.
 
Comment out this line:
```
hiddenmenu
``` by adding 2 # before the line.
 
Also you might want to increase the timeout from 3 seconds to atleast about 10 seconds, so you get enough time to choose your OS.

---

### Post by BHelts on 2007-06-12
Hey, thanks a lot for the help.  I think I've got it figured out.  I booted the LiveCD and had a look at GParted.  The / partition was not flagged as boot.  I did that and everything is working properly.  Thanks again for the help.

---

### Post by kittyhawk63 on 2007-06-12
Mark your thread as "Resolved."

---

### Post by BHelts on 2007-06-12
roger that kittyhawk.
perhaps you could tell me how to do that.
EDIT:  As you can probably see.... i got it.  thanks again for your help.

---

### Post by kittyhawk63 on 2007-06-12
> **BHelts said:**
> roger that kittyhawk.
perhaps you could tell me how to do that.
EDIT:  As you can probably see.... i got it.  thanks again for your help.

Sorry for the delay. I was installing a new DVD player.

Go to your first post on this thread. Select "Edit." Now select "Advanced Edit."
Go to the top and place a check mark in the first box for marking your problem as resolved. Click "Save."
kh

---

