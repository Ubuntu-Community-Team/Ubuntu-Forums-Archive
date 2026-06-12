---
title: "Rash Ubuntu install, failed duel boot"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by OperaSinger on 2007-10-17
I installed Ubuntu earlier today on a 50gb partition off the excess space from my windows partition. Ubuntu runs perfectly and all my windows files are still there on their partition, I can access them and such. But when I turn on my  computer and choose what to boot from, windows won't work. It just 

> Starting up....
_

Nothing happens from there. I'm not sure what went wrong, windows is still there with all the files, just won't boot for me.

---

### Post by ghost_ryder35 on 2007-10-17
did you defrag your hard drive a few times before doing this install?

---

### Post by OperaSinger on 2007-10-17
oh course not, but it was very clean

---

### Post by Duck2006 on 2007-10-17
From the terminal in ubuntu type

sudo fdisk -l

and post the output

---

### Post by OperaSinger on 2007-10-17
done
> 
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18945   152175681    7  HPFS/NTFS
/dev/sda2           23757       24321     4538362+   5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda3           18946       23756    38644357+  83  Linux
/dev/sda5           23969       24321     2835441   82  Linux swap / Solaris
/dev/sda6           23757       23968     1702827   82  Linux swap / Solaris

Partition table entries are not in disk order


---

### Post by ghost_ryder35 on 2007-10-17
> **OperaSinger said:**
> oh course not, but it was very clean

could be your problem right there.  Windows places files all over the place.  If you shrunk a partition before defraging you could of permentatly lost some boot files....

---

### Post by OperaSinger on 2007-10-17
There is still 70 gb left on it, sure it's fine

But I was using Tinyxp not windows xp, so I am thinking that it just isn't listed.

On boot screen it shows ubuntu and microsoft windows xp professional, which I tried installing long ago but settled with tiny xp, a way to find if that is it?

---

### Post by Duck2006 on 2007-10-17
Looks like grub didn't load, you may have to reload grub again

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by OperaSinger on 2007-10-17
> **Duck2006 said:**
> Looks like grub didn't load, you may have to reload grub again

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Ubuntu boots, and I get the grub screen listing it along with Microsoft Windows XP Professional

---

### Post by Duck2006 on 2007-10-17
Ok can you post your menu.lst

---

### Post by OperaSinger on 2007-10-17
> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=0ab2cbe6-5cbd-4a53-beb7-edd2a15161b5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0ab2cbe6-5cbd-4a53-beb7-edd2a15161b5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0ab2cbe6-5cbd-4a53-beb7-edd2a15161b5 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0ab2cbe6-5cbd-4a53-beb7-edd2a15161b5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0ab2cbe6-5cbd-4a53-beb7-edd2a15161b5 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
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


I'm reading the GRUB link, maybe I will get answer in there somewhere. But you're guys help is most likely better

---

### Post by Duck2006 on 2007-10-17
You could try super grub and see it windoze will boot

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by OperaSinger on 2007-10-17
While looking in gparted to see if maybe I had wrong root I saw that it showed my windows partition not mounted and with one of those triangular warning icons and it said
> Unable to read the contents of this filesystem!
Because of this some operations may be unavailable.

Did you install the correct plugin for this filesystem?

Also, root was set correctly

---

### Post by Duck2006 on 2007-10-17
Have you tryed to do a repair from the xp installion cd. Sounds like you may have damaged your xp instalion. From your menu.lst and fdisk -l it looks like they are ok.

---

