---
title: "[SOLVED] HELP!  I've lost my Ubuntu drive!"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by anewguy on 2008-03-26
Long story short - I needed to reinstall Ubuntu.  Tried with the kubuntu 6.04 livecd, everything installed fine, then got grub error 18 at boot.  Went clear back to where I started:  installed Windows 98SE on a 14gig drive (only drive installed at the time), then hooked up the larger drive I had been using for Ubuntu (80gig Maxtor) and installed Gutsy.  This duplicated how I first installed things to begin with.  Still getting grub errors.  I even reset the bios in case I had walked on something there.  Still no go.  Can boot from the liveCd (it's what I'm using now), install Ubuntu to the drive with no problem, but end up not being able to boot Windows or ubuntu due to the grub error.  I've looked up the error and it's trying to say the disk is larger than what my bios supports (max of 32gb).  This all worked before just fine.  Now I can't get Windows or Ubuntu either one!

Help!!  :)

---

### Post by smoker on 2008-03-26
just a suggestion, you may need an update for windows98se to recognize drives over 32GB, and/or sometimes you have to use jumpers on the drive, or change a setting in the bios for the same issue,

best of luck

---

### Post by Arthur Archnix on 2008-03-26
Abandon windows 98. Microsoft has.

Back up your data. Do a clean install of Xubuntu and tell it to use the entire disk. Download and use the alternate cd to accomplish this.

---

### Post by anewguy on 2008-03-27
Well, Windows 98Se, while ancient, isn't the problem in this case.  It's the BIOS on my computer.  you see, Windows is on it's own tiny 14gig drive and knows nothing of the ubuntu drive.  Ubuntu is on an 80 gig drive by itself.  The only thing they share in common is at boot - since the tiny drive with Windows on it is my "master" on the IDE bus (it won't work with the Ubuntu drive as the master for some reason).  At boot, the Windows drive mbr is saying to use grub and that grub is located on drive "x" (the ubuntu drive).  For some reason, even though this was working before, the BIOS has decided it can't address a drive that big and therefore grub bombs out on error 18.

With that said, can anyone help me figure out what the heck happened?  All I did was reinstall Ubuntu on the same drive configuration and now it doesn't want to work.  I've seen things on the net from Maxtor saying to set the geometry for my drive in the bios at certain settings, but my BIOS doesn't have those settings and apparently won't let me enter them manually.

HELP!!  I've already lost everything - I need to get a booting system again!

---

### Post by anewguy on 2008-03-27
Here's a dumb question - can I use a driver overlay program like maxblast and still be able to install Ubuntu to that drive?

---

### Post by mips on 2008-03-27
Try [http://sourceforge.net/projects/gag](http://sourceforge.net/projects/gag)

Dunno if it will solve the bios issue though.

---

### Post by Arthur Archnix on 2008-03-27
Boot a livecd then run and post the output of:
```
sudo fdisk -l
cat /change-this-to-path-to-drive/boot/grub/menu.lst
```
When you boot a live cd your hard-drives get mounted to special places. Perhaps under /media or under /mount.

---

### Post by anewguy on 2008-03-27
Made e temp directory, then mounted /dev/sdb2 to it, then ran gedit and copied the contents here.  I think it shows everything correctly - my BIOS seems to be getting in the way now for reasons I don't understand.  Worked in this exact configuration until I had to reload.  Here's a dumb question - if I ran fdisk on the large disk while in MSDOS (booting from a Windows 98SE boot diskette) is it possible I messed the disk up some how with "large disk support" enabled?  I thought that the variant of parted (be it qtparted, gparted, whatever as the front end) would take care of all of that.  At any rate, here's menu.lst:

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
# kopt=root=UUID=e9afcff2-7eba-431a-961d-7fbed01ee061 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e9afcff2-7eba-431a-961d-7fbed01ee061 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e9afcff2-7eba-431a-961d-7fbed01ee061 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows 95/98/Me
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by anewguy on 2008-03-28
Can anyone help on this?  I think somehow my BIOS is no longer letting me access the large drive because it is > 32gb, an old BIOS issue.  I assumed I didn't have it since this exact setup on this exact PC had been working until I had to reinstall Ubuntu - now everything is lost.  I've tried multiple settings in the BIOS for the drive, including setting the geometry manually as suggested by Maxtor (my80 gig drive is Maxtor).  Nothing seems to help - I either get grub error 5 or grub error 18.

I'm in desperate need of help here.  Without working through this I lose the ability to use my 80gig drive.

---

### Post by anewguy on 2008-03-29
Well, THIS IS NOT SOLVED, but I'm marking it as so to close it out.  I did a hard reset of the BIOS (i.e., the motherboard jumper) and now I can't access my hard disks at all.  All I can do is run on the LiveCD.  My motherboard - Biostar M5TZA (uses the 440bcz chipset) - is no longer supported by Biostar, so I have no idea where, if even, I'm going to be able to find a BIOS flash for it.:(

---

