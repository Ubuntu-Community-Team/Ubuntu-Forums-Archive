---
title: "HORRIBLE! Can't boot into computer anymore."
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2007-09-06
I have an x60 tablet. 
I followed the instructions on how to install 7.04 onto my laptop from a usb stick. My computer has no cd drive.

It was wierd because during the install I had to be connected to the internet for some reason or things would fail. Maybe I accidentally did a net install?

Anyways.. The point is, now when i turn on my computer withOUT the usb stick I get an error (error loading operating system.)

But if I put the stick in, then I can select between windows and ubuntu! (the grub menu comes up)

This is horrible guys, I feal like i messed up my disk. :(


Please help.

UPDATE: Installing (or reinstalling GRUB doesn't work)

---

### Post by bigken on 2007-09-06
you wrote the grub menu to the usb drive look up how to fix grub

---

### Post by southernman on 2007-09-06
Don't fret...

You just installed grub to the stick and not the hard drive.

Have a look at [Hermanzone's Super Grub Disk Page]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") to correct the snafu.

Welcome to Ubuntu!
:)


> you wrote the grub menu to the usb drive look up how to fix grub

Geesh, that was insightful! OP will be owe you his first born! :p jk

---

### Post by systemintheglitch on 2007-09-06
So could I just remove the usb, once ubuntu is booted and reinstall grub?

---

### Post by southernman on 2007-09-06
Don't see why you couldn't... nor why I didn't suggest it!

---

### Post by svalding on 2007-09-06
Welcome to the world of GRUB and Ubuntu. Follow that link a few posts up, it's pretty good. I've gotten out of worse pickles than this, GRUB's pretty simple once  you understand it.

---

### Post by systemintheglitch on 2007-09-07
HELP! 

UPDATE: It said i allready had GRUB Installed! So I tried reinstalling grub and that didn't work!

Could someone help? Im kind of a noob!

---

### Post by forestpixie on 2007-09-07
are you in ubuntu, if you are paste you're menu.lst here

open a terminal and do this 

```
cat /boot/grub/menu.lst
```

---

### Post by bigken on 2007-09-07
ignore me i did'nt see the above post

---

### Post by systemintheglitch on 2007-09-07
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
#      password --md5 $1$gLhSENSOREDbySYSTEMINTHEGLITCH
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
# kopt=root=UUID=716493b6-3c36-4612-80dc-6942263e3da4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=716493b6-3c36-4612-80dc-6942263e3da4 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=716493b6-3c36-4612-80dc-6942263e3da4 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, memtest86+
root            (hd1,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Windows Vista/Longhorn (loader)
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title           Windows Vista/Longhorn (loader)
root            (hd1,1)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

---

### Post by forestpixie on 2007-09-07
sorry meant to get you to do this too 

sudo fdsik -l

---

### Post by systemintheglitch on 2007-09-07
HERE::

WHEN I HAVE THE USB STICK IN:
sudo fdisk -l gives:

**********************************************************
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         634     5087232   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         634        8220    60937500    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            8221        9660    11559240   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4            9660        9729      559440    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5            9660        9729      559408+  82  Linux swap / Solaris

Disk /dev/sdb: 2055 MB, 2055021056 bytes
255 heads, 63 sectors/track, 249 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         249     2000061    6  FAT16

********************************************************

I think sdb1 is my usb stick.


Thank you for your help by the way! :)

---

### Post by forestpixie on 2007-09-07
I'd wait for another opinion - because I'm not completely certain. Firstly can you actually boot vista? Secondly I assume you have only the one hdd.- is that correct?

> Device Boot Start End Blocks Id System
/dev/sda1 1 634 5087232 27 Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2 * 634 8220 60937500 7 HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3 8221 9660 11559240 83 Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4 9660 9729 559440 5 Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5 9660 9729 559408+ 82 Linux swap / Solaris

/dev/sdb1 * 1 249 2000061 6 FAT16

```

title Ubuntu, kernel 2.6.20-16-generic
root (hd1,2)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=716493b6-3c36-4612-80dc-6942263e3da4 ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root (hd1,2)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=716493b6-3c36-4612-80dc-6942263e3da4 ro single
initrd /boot/initrd.img-2.6.20-16-generic

title Ubuntu, memtest86+
root (hd1,2)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Windows Vista/Longhorn (loader)
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title Windows Vista/Longhorn (loader)
root (hd1,1)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

I think that the first 2 partitions on your hard drive are for win, have you a recovery partition? - fdisk recognises these as sda1 and 2

sda3 is the linux partition and sda 4 is an extended partition holding the swap partition sda5.

Your menu.lst says to me that it's expecting to find both ubuntu and vista on the usb stick - that would be some memory stick :) ? THAT is what I'm a bit worried about, 

 if this was my pc I would change all of the  

(hd1,2) to (hd0,2) in your menu.lst to boot ubuntu and change the vista items there to read (hd0,0) and (hd0,1) respectively.

I would be inclined to wait now - see what replies you get. I would really hate to chuck you in a hole with this.

---

### Post by southernman on 2007-09-07
Ok systemintheglitch... first things first! DO NOT PANIC! I'll get you out of this relatively painless(ly).
 
First I need to know what you have installed on /dev/sda2. I'll assume that it is the old Windows XP installation that came with your laptop. The second assumption I'll make is that /dev/sda1 is a recovery partition setup by the maker of your laptop... that's a common thing and if your not going to use the manufactures system restore cd's then you could safely delete that partion all together... same for /dev/sda2 if you don't intend to run a dual boot setup. HOWEVER, that is NOT the focus of your fact finding mission here and now. Another thing to tackle at a later date... comprehendo? ;) thought so.

The following link will walk you through reinstalling grub. Although the title of the page says "Reinstalling Grub from a LiveCD," the same steps apply to doing this from the command line on a fully working system. I've had to do it a few times myself! :p

[REINSTALL Grub]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD").  

If you like, and we can meet on IRC (schedules allowing), then I'll be happy to walk through it with you. Let me know either by PM, email, or posting in the thread.

BTW, The "it says grub is already installed" part, confuses me a little (whats new), but we don't really care about that... we're gonna reinstall it, whether your system goes kicking and screaming or not!

Don't worry pal... we'll get it fixed.

---

### Post by systemintheglitch on 2007-09-07
Before I do anything like try to reinstall grub (allthough I though i allready did that through the package manager), I would like to share some better info about my harddrive.. I believe you were asking about which mount points correspond to which partitions..

By the way, I need to keep ALL of my partitions, so..

```

Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda3     ext3    11377600   3160652   7638988  30% /
varrun       tmpfs      513224       100    513124   1% /var/run
varlock      tmpfs      513224         0    513224   0% /var/lock
procbususb   usbfs      513224       120    513104   1% /proc/bus/usb
udev         tmpfs      513224       120    513104   1% /dev
devshm       tmpfs      513224         0    513224   0% /dev/shm
lrm          tmpfs      513224     33788    479436   7% /lib/modules/2.6.20-16-generic/volatile
/dev/sdb1     vfat     1999776    723328   1276448  37% /media/disk
/dev/sda1     ntfs     5087228   4335128    752100  86% /media/ServiceV002
/dev/sda2     ntfs    60937496  35558028  25379468  59% /media/SW_Preload


```

->Now since my usb stick is plugged in sdb1 is my usb stick.
->sw_preload is my vista partition which is very important that i keep.
->ServiceV002 = sda1 is my resotore partition which is important because I have no cd drive! :)


If noone has any objections I will try that grub reinstalation tutoriall.
Thank you and please check back here to see if it worked!
Thank you!

---

### Post by systemintheglitch on 2007-09-08
Now it gets worse..

Those instructions didn't work..
 
Heres what I did like it said:
```


grub> find /boot/grub/stage1
 (hd0,2)

grub> root (hd0,2)



```

There was no console response from that last command..
Here is my grub menu.lst

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# kopt=root=UUID=716493b6-3c36-4612-80dc-6942263e3da4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=716493b6-3c36-4612-80dc-6942263e3da4 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=716493b6-3c36-4612-80dc-6942263e3da4 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, memtest86+
root            (hd1,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Windows Vista/Longhorn (loader)
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title           Windows Vista/Longhorn (loader)
root            (hd1,1)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1



```

NOW after running that grub command, it LOOKS like grub loads up fine without the USB stick.. but then when I select an OS to boot into from the grub menu it gives me error number 21..

Which the documents say (about error number 21)
```

21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 


```

Man I just want my computer to boot up normally.
:(

---

### Post by systemintheglitch on 2007-09-08
Okay, so heres what I did to get grub to boot the linux partition.. I changed the hd1 to hd0 in the menu.lst file..

What should I do to the windows entries to get the windows partions to boot?

Thank you so much for all your help everyone.

---

### Post by forestpixie on 2007-09-08
firstly is that you're NEW menu.lst 2 posts up

secondly - can you start vista

Edit - to get the windows 

root            (hd1,0) change to root            (hd0,0)
root            (hd1,1) change to root            (hd0,1)

Basically linux counts from 0 - so when you installed the USB must have been counted as the first drive, therefore the hdd was number 2 - (hd1,0) the second number being the partition
Take the USB away and while the system waits busily for the first disc - menu.lst is telling it to look for a non existent second drive

---

### Post by systemintheglitch on 2007-09-08
I tried that last night. That didnt work.

It gave a wierd windows loader error.

---

### Post by systemintheglitch on 2007-09-08
Here is the specific error i get when i change to hd0 for the windows entries..

```
Windows boot manager
Windows failed to start...bla bla bla.. could be hardware error bla bla...



File: \Boot\BCD

Status: 0xc0000001

Info: An error occured while attempting to read the boot configuration data.



```

---

### Post by forestpixie on 2007-09-10
what have you got in here - 

/boot/grub/device.map

---

### Post by onlyconnect on 2007-09-10
> **systemintheglitch said:**
> I have an x60 tablet. 
I followed the instructions on how to install 7.04 onto my laptop from a usb stick. My computer has no cd drive.
I had similar problems installing onto a Tosiba table with no CD drive:

[http://www.itwriting.com/blog/?p=307](http://www.itwriting.com/blog/?p=307)

As you can see, I fixed it first with the Super Grub Disk:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

and then by editing menu.lst.

Hope this is some help.

Tim

---

### Post by systemintheglitch on 2007-09-10
> **forestpixie said:**
> what have you got in here - 

/boot/grub/device.map



Why would this matter: here it is:

```

(hd0)	/dev/sda
(hd1)	/dev/sdb

```

---

### Post by forestpixie on 2007-09-11
> Why would this matter

Just checking really - I can see that you've tried changing menu.lst to suit but have you tried using the supergrub livecd?

Don't know that I'm going to be able to help much more to be honest :(

Edit - in fact I'm not so sure that the hd1 line should be there, that's your usb

---

### Post by systemintheglitch on 2007-09-12
thats the thing.. 

I don't have a cd-drive! Its a lenovo tablet pc.

---

### Post by forestpixie on 2007-09-12
> 
I don't have a cd-drive!

I know - it seems to map the usb - but it's not plugged in I assume - that's why I mentioned it, I wonder if that's what's causing the boot to fail. Although I've got to say I'm not sure. Logically it should all work - grub is looking at hd0 - which is you're hard drive. 

I'm amazed at your patience - I would've started again by now. And the supergrub livecd doesn't work? - Or have you not tried that?

---

### Post by systemintheglitch on 2007-09-12
So.. if you look at menu.lst
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title Windows Vista/Longhorn (loader)
root (hd1,1)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

Whats with map hd0 to hd1??
And maybe that combined with the fact that usb is mapped to hd1?

The linux entry works! But maybe that's because it doesn't have that map entry in menu.lst?
What do you think?

---

### Post by systemintheglitch on 2007-09-12
Also, 

do you recommend that i delete the hd1 from device.map?

---

### Post by bigken on 2007-09-12
> **systemintheglitch said:**
> thats the thing.. 

I don't have a cd-drive! Its a lenovo tablet pc.


you could buy and external usb dvd cdrw this could only be an asset they are as cheep as chips these days

---

### Post by forestpixie on 2007-09-12
> root (hd1,1)

if your menu.lst still tells that Vista is on hd1 then I suspect that could be the problem, although from an earlier post I believe you said it didn't work.

> Whats with map hd0 to hd1??

I've seen it before with regard to vista on a menu.lst - but I have no idea what it's about - last version of windows I used was win2000.

If the linux entry works - but vista won't it wouldn't hurt to try to comment those map lines out (I think!) - if you # in front it'll be easy enough to remove it if you need to.

bigken was looking - perhaps he'll look again. I'm getting lost now - not sure thatI'll be able to add much .

---

