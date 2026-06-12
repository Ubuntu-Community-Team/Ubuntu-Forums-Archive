---
title: "Help! Vista Won't Startup After Installing Ubuntu 7.10"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by arthrane on 2007-11-23
--Originally posted in General Help forum, but received no replies and it's getting buried in there. Please respond!--

There seem to be aplenty of related threads, but none have helped. I'm usually not much of a geeky person, so excuse my muddled thoughts.

I installed from the live CD, and followed the defaults. (I've been told I should have partitioned *manually* first, but alas, I did not. But that does not tell me what to do now.) When I start-up, I get the GRUB with Ubuntu, Ubuntu (recovery), Ubuntu memtest, and Windows Vista/Longhorn (loader). Ubuntu works like a gem, but if I try to run Windows Vista it goes into recovery mode. When it asks which OS to repair, Vista doesn't show up.

If I go to Computer, I see multiple partitions (or at least, I think I do!). One of them is in essence the C: drive, and old files still show up. Another one is Filesystems, and it seems to hold the things for Ubuntu.

One of the friends I asked for help (but we are still unable to resolve the problem) told me to copy these in, so here it is:

arthrane@arthrane-laptop:~$ sudo fdisk -l
[sudo] password for arthrane:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0779162

Device Boot Start End Blocks Id System
/dev/sda1 1 192 1536000 27 Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2 * 192 7037 54982422 7 HPFS/NTFS
/dev/sda3 7038 9611 20675655 83 Linux
/dev/sda4 9612 9729 947835 5 Extended
/dev/sda5 9612 9729 947803+ 82 Linux swap / Solaris
arthrane@arthrane-laptop:~$
arthrane@arthrane-laptop:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e8bd62f3-d83c-4f79-9c9c-292c91ba29cb ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=e8bd62f3-d83c-4f79-9c9c-292c91ba29cb ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=e8bd62f3-d83c-4f79-9c9c-292c91ba29cb ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,2)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows Vista/Longhorn (loader)
root (hd0,1)
savedefault
makeactive
chainloader +1

arthrane@arthrane-laptop:~$ uname -a
Linux arthrane-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

As a last sidenote, I do not have the CDs for XP or Vista with me, although I suppose I'll have to scrap them up if absolutely necessary.

Any help would be enormously appreciated! :)

---

### Post by LaRoza on 2007-11-23
You can and should get the super grub disk. If all else fails, restore the Windows boot loader.

You should have used Vista's Disk Management to shrink the partition.

Add this to the end of menu.lst

```

gksudo gedit /boot/grub/menu.lst

```

> 
title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1


That might work....

Please give more detailed information about how many disks you have, and what the partitions are.

---

### Post by arthrane on 2007-11-23
When I try that, I get BOOTMGR is missing - Ctrl-Alt-Del to restart.

I'm not sure what you mean about hard drives or partitions... considering I simply followed defaults. I think I only have one hard drive, though. As for partitions, in Computer, I see three things (other than CD/DVD stuff), namely something which holds everything from C: (34.4 GB out of 52.4 used, Filesystem type ntfs), a TOSHIBA SYSTEM VOLUME (138.3 MB used out of 1.5 GB, Filesystem type ntfs), and Filesystems(3.0 GB used out of 19.4 GB, Filesystem type ext3), which holds Home and suchlike. 

=/ I hope that's what you mean.

---

### Post by meierfra on 2007-11-23
> Partition 1 does not end on cylinder boundary.
This might be the cause of  your problem, and I don't know  how to fix this.  You really should have used  Vista to shrink your Vista partition. 

But you might give this a try: 

change "root" to "rootnoverify" so that your windows item looks like:

title Windows Vista/Longhorn (loader)
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1

---

### Post by arthrane on 2007-11-25
I've tried those - no luck.

[http://ubuntuforums.org/showthread.php?p=2527751](http://ubuntuforums.org/showthread.php?p=2527751) worked though... once only! Then my computer started restarting infinitely.

:cry:

---

### Post by meierfra on 2007-11-25
> [http://ubuntuforums.org/showthread.php?p=2527751](http://ubuntuforums.org/showthread.php?p=2527751) worked though... once only! Then my computer started restarting infinitely.

What worked? The method in Eatingorange post [31]("http://ubuntuforums.org/showthread.php?p=2527751#31").  ?

Did you try the procedure more than once?

---

### Post by Sef on 2007-11-25
> You can and should get the super grub disk.

[Super GRUB Boot Loader]("http://supergrub.forjamari.linex.org/").

---

### Post by arthrane on 2007-11-25
I reinstalled grub ([http://my.opera.com/Mr%20Green/blog/show.dml/224803](http://my.opera.com/Mr%20Green/blog/show.dml/224803)).

It worked! Thanks everyone for the help! :KS

Now I just have to shut up that naughty go-dual-boot-on-your-other-computer voice in my head until next weekend and get some work done.

---

### Post by arthrane on 2007-12-28
* sigh *

I'm having the infinite restarting loop again. The temporary fix is reinstalling GRUB (I do this from the live CD). Unfortunately, GRUB is breaking after one or two restarts every time.

So my options are either fixing this, or removing Ubuntu so that I don't need GRUB (Dad insists on having Vista). I of course, would prefer a fix! =)

---

### Post by meierfra on 2007-12-28
Try[ EasyBCD]("http://neosmart.net/dl.php?id=1")

---

### Post by talsemgeest on 2007-12-28
It seems to me that you are stuck with ubuntu now. If you try to get rid of it, the grub wont work and even reinstalling the vista bootloader wont fix it.

---

### Post by talsemgeest on 2007-12-28
Getting rid of Ubuntu will stuff up your computer even more. It will make your computer unbootable

---

### Post by arthrane on 2007-12-28
I'd need to put Windows back in charge of the MBR, yes. But I'm quite sure I wouldn't kill the computer if I did kill Ubuntu.

---

### Post by meierfra on 2007-12-28
Did you look at EasyBCD. I'm sure it will solve your problem

---

### Post by arthrane on 2007-12-28
Well, I downloaded it. I just have no idea what to do, so I'm trying to figure that out at the moment.

Thanks though. =)

---

### Post by arthrane on 2007-12-28
I put the Windows bootloader back into control of the MBR.

Well, it's working!

Thanks so much for the help! :)

---

