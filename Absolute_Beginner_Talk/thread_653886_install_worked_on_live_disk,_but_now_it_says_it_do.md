---
title: "install worked on live disk, but now it says it doesn't even exist"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by jart16 on 2007-12-30
Sorry for being a total noob, but I might be missing something...

Here's what I'm trying to do:
-I have 2 hard disks, a 30 gig and a 100 gig... the 100 i use for Windows XP
-The XP is the master and the one I am going to put ubuntu on is the slave

Main Hardware:
-MSI K8N NEO4 Motherboard
-AMD Athlon64 3500+

Yes, I know the disk is working because the live CD detects it, and windows detects it

I installed the live disk just fine... hardware worked, internet worked, and the installation seemed successful... it then said to remove the disk, then start up again
I start up, and the thing skips the bootloader and takes me right to my windows hard drive like the ubuntu disk never existed
how do i get it to run ubuntu without having to take out my 100 gig harddrive

thanks for dealing with me :lolflag:

---

### Post by bone2006 on 2007-12-30
It's possibly where you installed the grub boatloader.  With multiple partitions I've had older versions of redhat install on a strange partition when I had a few hard drives and then when it rebooted it would go straight into windows.  
I'd give supergrub a chance or maybe somebody else can help you better

---

### Post by philinux on 2007-12-30
If it installed ok then if you go into the bios and make the ubuntu disk the master and windows the slave it might just sort it out.

Worth a try as it's easily reversed.

---

### Post by ajgreeny on 2007-12-30
Boot the live CD again and in terminal type ```
sudo fdisk -l
``` and then show us the output from that.
Mount the ubuntu hard disk partition using the ubuntu live environment and look for **/boot/grub/menu.lst** and copy that so we can see it.
It does sound as though you put grub somewhere else than the windows mbr, as your machine went straight to windows without grub, but it will be interesting to have a look at those two things I asked for.  If that turns out to be the problem we can easilly put it right with the live CD again.

Useful things, these live CDs aren't they?

---

### Post by jart16 on 2007-12-30
ok im posting this from the live disk...
i typed in your code and it gave me:

ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

As for the menu:

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
# kopt=root=UUID=396d98de-aff0-4130-9445-91d3d47e91cb ro

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=396d98de-aff0-4130-9445-91d3d47e91cb ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=396d98de-aff0-4130-9445-91d3d47e91cb ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

(sorry if that was a little too much info):confused:

---

### Post by jart16 on 2007-12-30
something look wrong?

---

### Post by autocrosser on 2007-12-30
According to your menu.lst---your master is the one Ubuntu is on & the slave is Windows---hd0,0 is Ubuntu & windows is hd1,0

Verify that your drives are really set as master-slave or cable select.

If you are sure that the drives are correct, you can try reversing the hdx,x

edit hd1,0 to hd0,0 & same for the reverse

you can also take a look at:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by jart16 on 2007-12-30
ok tried your link
nothing happened

then i tried editing the menu.lst
and it wouldnt let me save... it said i "don't have privelages"

---

### Post by autocrosser on 2007-12-30
Take a look at Tutorials & Tips---the thread is: How to install Grub from a live Ubuntu CD.

I'll try the thread link again:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by jart16 on 2007-12-30
i already tried that...
nothing...

---

### Post by Paqman on 2007-12-30
> **jart16 said:**
> 
then i tried editing the menu.lst
and it wouldnt let me save... it said i "don't have privelages"

To open your text editor as root use:

```

gksudo gedit *name_of_file*

```

Whenever you're told you don't have sufficient privileges it's generally because that file is owned by "root", so you can't edit it as a user. sudo/gksudo temporarily gives you root privileges. Use with care!

---

### Post by ajgreeny on 2008-01-01
Sorry, not been online much - Christmas etc etc. 
>  ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- 1The last bit of that was a lower case L, not 1 as you used.  Try again and you will get an output which should be useful.

---

