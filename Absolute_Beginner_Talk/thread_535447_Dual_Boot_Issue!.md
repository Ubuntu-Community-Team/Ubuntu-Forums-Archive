---
title: "Dual Boot Issue!"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-08-26
hey guys quick question here i have ubuntu and vista dual booting on my laptop and the other day i was in vista everything working fine then i booted into ubuntu and everything was fine then i went to boot back into vista and it sends me on the inevitable reboot loop whenever i select vista from GRUB.  I was thinking it might have something to do with GRUB trying to mount the wrong partition or something but i haven't made any changes to any of them since the last time i booted into vista.  Any ideas or help would be greatly appreciated!  Thanks, Alain

---

### Post by weatherman1293 on 2007-08-26
That's vista for ya.

I've had vista collapse on it's own.

---

### Post by khughitt on 2007-08-26
You can still boo into linux, right?

Post your partition info & grub menu file contents online-- to get the partition info, open a terminal and type:

```
sudo /sbin/fdisk -l
```

The grub menu file is located at

```
/boot/grub/menu.lst
```

First we can double check to make sure all of the boot-load information is correct. If everything there looks okay, you may consider trying to boot off of the Vista CD and see if it can restore the install.. I haven't used Vista before though so I can't tell you too much about how you would go about doing that.

---

### Post by S15_88 on 2007-08-26
here we go:

> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *        1312        5844    36411322+   7  HPFS/NTFS
/dev/sda3            5845       19457   109346422+   5  Extended
/dev/sda5            5845       17998    97626973+  83  Linux
/dev/sda6           17999       19261    10145016   83  Linux
/dev/sda7           19262       19457     1574338+  82  Linux swap / Solaris


and...

> 

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
# kopt=root=UUID=ab5a2558-1345-48e9-bb01-833b499f021a ro

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ab5a2558-1345-48e9-bb01-833b499f021a ro irqpoll
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ab5a2558-1345-48e9-bb01-833b499f021a ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ab5a2558-1345-48e9-bb01-833b499f021a ro
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ab5a2558-1345-48e9-bb01-833b499f021a ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1



Thanks again for the help!

---

### Post by S15_88 on 2007-08-26
from the menu.lst it says #on /dev/sda3 but it's actually on /dev/sda2  but that part is commented out so it shouldn't matter?  i'm a little puzzled why won't it boooooot!

---

### Post by khughitt on 2007-08-27
The commented line itself doesn't do anything but it does suggest that grub might be looking for windows in the wrong place. From the fdisk results however it looks okay, but you can try changing it anyways to see if it helps.

What you can do is restart your machine and let grub load up. Then in grub, move the selection over the windows line, and hit "e" to edit the command. It should show the parameters from your grub configuration:

```

root (hd0,1)
savedefault
makeactive
chainloader +1

```

Move the selection over the first line, root(hd0,1), and hit "e" again to edit that line. Try changing it to different things like (hd0,2). When you are done editing, hit enter to save the line, and then "b" to boot. The changes aren't permanent so it is a good way to test out different settings for grub.

You can also try removing the savedefault or makeactive lines to see if that helps. I'm not really sure what they do to be honest, but there it couldn't hurt to try.

Finally if you still are not able to get windows to load again after playing with these settings, your best bet is probably just to boot onto the windows Vista CD and try and recover the windows install.

If anyone else has Vista and has an experience with this, feel free to chime in :)

Goodluck!

---

### Post by carverj on 2007-08-27
I don't know if this helps, but if the partitioning and grub is fine, could be a fault with Vista. Does it try to boot Vista and then ... *click* reboots?
Is it trying to configure it's updates?

---

