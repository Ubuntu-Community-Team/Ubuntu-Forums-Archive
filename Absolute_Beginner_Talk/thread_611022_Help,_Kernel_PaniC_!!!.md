---
title: "Help, Kernel PaniC !!!"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by 01100001 on 2007-11-12
I have dual boot: XP and Ubuntu 7.10 ... today when I tried to start ubuntu it didn`t want to load..
then I tried ti start id in recovery mode and I got this message:

run-init: /sbin/init: Exec format error
[      5.084888] Kernel Panic - not syncing: Attempted to kill init!

Is there a way to FIX THIS !!! HELP!!!
I spend ages trying to configure the ubuntu the way I like it .. 

If there is no way to fix thhis.. bye bye Ubuntu and Linux for EVER!!!! >.. i`m really MAD about this error !!!!!!! :mad::mad::mad::mad::mad::mad::mad::mad:

---

### Post by Pumalite on 2007-11-12
Post your specs. You might need the Alternate CD. Do md5sum on your iso and burn at 4x, check for CD integrity before install.

---

### Post by 01100001 on 2007-11-12
Oh.. I had Ubuntu installed for 2 weeks and it didn`t made any problems.. 

Here are my specs of the hardware:

CPU- Intel DuoCore 2.66GHz 2x1MB Cache
MB- Intel
VGA- nVidia GeForce 71--GS
HDD- 160GB western Digital
RAM- 1GB 667MHz DDR2

---

### Post by Pumalite on 2007-11-12
If you had Ubuntu installed; what were you doing in the OS before this happened?

---

### Post by 01100001 on 2007-11-12
nothing today .. just surfing the web.. 

there was some odd error from the 'ls' in terminal . something for the color .. but.. nothing unusual

---

### Post by mysticrider92 on 2007-11-12
Can you post your /boot/grub/menu.lst? It sounds like you are not loading an initrd on boot, which is needed to load the kernel.

---

### Post by 01100001 on 2007-11-12
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


splashimage=(hd0,5)/boot/grub/Blu.xpm.gz

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
# kopt=root=UUID=d31bf7f2-11ed-49c4-b21e-ef4be29522fb ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d31bf7f2-11ed-49c4-b21e-ef4be29522fb ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d31bf7f2-11ed-49c4-b21e-ef4be29522fb ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
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



Any idea ??? :confused::confused::confused::confused:

---

### Post by mysticrider92 on 2007-11-12
Hmm, the problem does not look like your initrd. Are there any other errors during the boot? The kernel panics are never well explained, but there might be some hint.

One of the most likely problems could be a bad install cd, the files might have been installed wrong.

---

### Post by 01100001 on 2007-11-12
no.. no other error during boot.. and I have installed this ubuntu from that CD on many computers..
and non of them show this problem .. can I do somekind of a recovery ? or rollover ?

Or even better, is there a way to fix this?

---

### Post by 01100001 on 2007-11-13
anyone ??

---

### Post by eldragon on 2007-11-13
insert the install cd, and run memtest, you might be looking at a hardware issue here

---

### Post by ByteJuggler on 2007-11-13
> **01100001 said:**
> 
run-init: /sbin/init: Exec format error


This means the kernel couldn't execute /sbin/init, it may be corrupt/have become corrupted or it may be having some other problem executing it. "init" is the "root process" the father of all other programs running on the system.  If it won't start then the rest of the system won't start.

> **01100001 said:**
> 
[      5.084888] Kernel Panic - not syncing: Attempted to kill init!


This is saying that because of the preceding error(s) the kernel is stopping writing to disk (syncing) for safety's sake.

You will have to try and establish whether there's something wrong with your "init", so can you boot off of a liveCD and can you see your existing partition mounted under /media?

Also, did you do anything at all before this started, no matter how insignificant it may seem to you?  Did you install any updates for example?

---

### Post by pds on 2008-01-18
Hi!

Yesterday I had exactly the same problem, has anyone found a solution?

---

