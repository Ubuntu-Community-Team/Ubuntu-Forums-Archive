---
title: "Linux---Windows---Linux.. dual booting is hard?"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by KIFIKA on 2007-03-02
Okay, first i had a working copy of ubuntu on my system. When i installed windows (exclusively just for photoshop) I lost my GRUB, and wasn't able to start Ubuntu. When i made a post, i installed SuperGRUB and was able to recover Ubuntu after a couple of failed attempts, but now i have no idea how to get windows to start.. 

any one know how i can get both to start and function propperly?

Best regards, 

KIFIKA

---

### Post by dstew on 2007-03-02
I assume you are now booting with Grub. If so, you need to add a windows boot item to your Grub menu list by editing the list file, /boot/grub/menu.lst. You would add a Windows boot item, like this (if the bootable windows partition is hd0,0):

title Windows XP #or whatever
root   (hd0,0)
makeactive
chainloader +1

After you save the file, and reboot, you should have the Windows item to select on your Grub boot menu.

---

### Post by bodhi.zazen on 2007-03-02
Boot Ubuntu

Post /boot/grub/menu.lst

and output of :

sudo fdisk -l

You likely need to add a stanza regarding Widows

Something like : 

title windows XP
root (hd0,0)
savedefault
chainloader +1

---

### Post by ellis rowell on 2007-03-02
I have both on my desktop, but I tackled it by having two hard disks. The power supply to the disks is controlled with a two pole two way switch to feed the 5v and 12v lines to either of the HDD's. To switch from one to the other, you have to close down, switch over and boot up the alternative disk. As I use files which are common to both systems, I keep these on an external USB HDD.

---

### Post by Scunizi on 2007-03-02
Unless you're a professional photoshop user or photographer using photoshop, you may want to spend some time getting use to Gimp.  As a photog (am/pro) myself, I've found gimp to be an invaluable tool that has more options than I typically need.  After installing my Wacom Graphire4 the whole experience took on new light.  Don't get me wrong.  Gimp is not the do all programs but might just suit your needs and eliminate your dual boot situation.  You may also want to look at VMWare Server for running windows inside of an Ubuntu window.  I do that with w2kpro just for two propriatory programs I use for Real Estate.  ......... I also dual boot for games when I have the time.  It's amazing how quick XP can appear when there's nothing really loaded on it. :)

---

### Post by KIFIKA on 2007-03-02
sorry it took so long guys i had to go get something at a friends house. Anyway here is my fdisk-l menu:

> root@nick-desktop:~# -fdisk
bash: -fdisk: command not found
root@nick-desktop:~# fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
root@nick-desktop:~# sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4916    39487738+   7  HPFS/NTFS
/dev/hda2            4917        4998      658665    5  Extended
/dev/hda5            4917        4998      658633+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9645    77473431   83  Linux
/dev/hdb2            9646        9726      650632+   5  Extended
/dev/hdb5            9646        9726      650601   82  Linux swap / Solaris


and here is the output of my menu.lst:

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
# kopt=root=UUID=45135a25-6bd8-49fb-b40e-943d7d508b56 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu, kernel 2.6.17-11-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=45135a25-6bd8-49fb-b40e-943d7d508b56 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=45135a25-6bd8-49fb-b40e-943d7d508b56 ro single
initrd		/boot/initrd.img-2.6.17-11-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=45135a25-6bd8-49fb-b40e-943d7d508b56 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=45135a25-6bd8-49fb-b40e-943d7d508b56 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.17-10-386 (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=82e7b8dc-3abe-4cdd-8068-3f8445b54d5a ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.17-10-386 (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=82e7b8dc-3abe-4cdd-8068-3f8445b54d5a ro single 
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.12-10-386 (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=UUID=82e7b8dc-3abe-4cdd-8068-3f8445b54d5a ro quiet splash 
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.12-10-386 (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=UUID=82e7b8dc-3abe-4cdd-8068-3f8445b54d5a ro single 
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.12-9-386 (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=UUID=82e7b8dc-3abe-4cdd-8068-3f8445b54d5a ro quiet splash 
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.12-9-386 (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=UUID=82e7b8dc-3abe-4cdd-8068-3f8445b54d5a ro single 
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, memtest86+ (on /dev/hda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot



@scunizi: Yea, photoshop is pretty much my life, i used to use it day in and day out. Gimp is too much of a transition for me to get use to and use i always find myself going "where is that.. oh there isnt " I've also tried VMWare, but when my computer is nothing short of suck-tacular.. its a gagillion years old ... anyway. When i tried running Photoshop with a screenrecorder for tutorials i was going to me... it was magnificently slow and would only record 1 frame per second :(

---

### Post by bodhi.zazen on 2007-03-02
You need to add a stanza for windows ...

dstew and I have both posted a stanza that will work ...

---

### Post by KIFIKA on 2007-03-02
Yea, i just tried it, when i tried to boot it , it told me unknown file type 0x73 or something to that effect.

---

### Post by bodhi.zazen on 2007-03-02
Please post the stanza you tried and if possible error message ...

---

### Post by KIFIKA on 2007-03-02
title windows XP
root (hd0,0)
savedefault
chainloader +1

after i put that in and rebooted, when it did the root command i gave me an error unknown system type x73 ( i believe it said something exactly, if not very similar to that)

---

### Post by bodhi.zazen on 2007-03-02
I tink you need to add "make active"

Like this :

title windows XP
root (hd0,0)
savedefault
**makeactive**
chainloader +1

---

### Post by KIFIKA on 2007-03-02
I tried that a little while ago, when i did a search, same problem.

---

### Post by Bartender on 2007-03-02
Both installs are relatively new, right?  I mean, what do you have to lose by starting over?  Wipe the drive, install Windows first, then install Ubuntu.  Your hassles will probly go away.  You might want to partition the disc first using GParted, or partition it during the Windows install.

---

### Post by KIFIKA on 2007-03-02
Sorry. Its just not an option. Actually that hda1 has only windows on it and hdb1 has only ubuntu on it, those old boot options are from a previous installation i had of Ubuntu on hda1. Anyway, Ubuntu has been on here a while, its not new and i cant loose all my stuff. 

> File type unknown partition type 0X7
what the "error"(?) i got after I tried booting from the winxp option and after the root command.

---

### Post by bodhi.zazen on 2007-03-02
Before you re-install ...

Can you boot to the live CD, look at your partitions with Gparted, I am not sure the information from fdisk is accurate ...

This may sound silly, but do you still have Windows installed, of did you install Ubuntu over the top of Windows ??

The reason I ask is these set of stanzas form your menu.lst :

[color=red]root (hd1,0)[/color]
kernel /boot/vmlinuz-2.6.17-11-386 root=UUID=45135a25-6bd8-49fb-b40e-943d7d508b56 ro quiet splash

And 

[color=red]root (hd0,0)[/color]
kernel /boot/vmlinuz-2.6.17-10-386 root=UUID=82e7b8dc-3abe-4cdd-8068-3f8445b54d5a ro quiet splash

---

### Post by KIFIKA on 2007-03-02
Okay, here is the story, i guess. First i had ubuntu on my hda1.. when i added a new harddrive, i installed ubuntu on it and went from there. Then i installed windows on hda1 over the ubuntu, but it deleted my GRUB so i couldnt boot ubuntu on my hdb. So when i used SuperGRUB and got it back, everything is there, but windows. 

Also, i deleted all those other options on hda since they all gave me errors, because ubutnu didnt exsist anymore.

---

### Post by bodhi.zazen on 2007-03-02
Does gparted still show windows partition ?

Can you mount it and confirm it is intact ??

Can you boot windows with super grub ???

---

### Post by KIFIKA on 2007-03-02
I can't boot from super grub, it just takes me back to the hd's GRUB menu with ubuntu and that nonworking windows selections on it. 

[http://img397.imageshack.us/img397/4961/screenshotnn0.png](http://img397.imageshack.us/img397/4961/screenshotnn0.png) 

idk if htat helps you any but thats a screenshot of my gparted

---

### Post by bodhi.zazen on 2007-03-02
Thanks ...

My only thought is to mount the partition and confirm the contents ...

---

### Post by KIFIKA on 2007-03-02
Sorry, how would i actually check to make sure its mounted? If it is unmounted, it would have to be due to SuperGRUB, same if any contents were deleted.

---

### Post by Scunizi on 2007-03-02
It looks like you have a mix of SATA drives and IDE Drives like I do.  I had some issues installing Ubuntu with a mixed configuration.  I actually have 2 SATA drives and an IDE installed.  With XP on SATA0 (1) and installing Ubuntu on SATA1 (2) it put grub on the IDE for some reason.  I had to disconnect the IDE and go through the process again to get it right then plug in the IDE. If I'd known more about grub and how to fix it, it would have been easier and less time consuming.  I'm sure the guys here will be able to straighten out your grub and get you working.  One thing I did learn with multiple drives is to install grub to all the primary drives that contain an operating system.  I did this as a backup just in case my XP drive dumped I could change the bios to boot directly to Ubuntu on the secondary.  I did this by following the information at [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm).  :idea:

Edit:  Sorry.  After relooking at your fdisk list I reallized that the mention of SATA drives was actually in referance to how to use fdisk.  However the link I provided may help you fix your issue.

---

### Post by KIFIKA on 2007-03-02
Lol, sorry it doesn't really help me because im not sure what my problem is and what im trying to fix.. sorry :( can you link me to a specific part or resource?

---

### Post by X-626 on 2007-03-02
I had a problem like that once, and I believe I solved it by using rootnoverify instead of root, so your XP boot stanza should be:
```
title windows XP
rootnoverify (hd0,0)
savedefault
chainloader +1
```Try that, and see if it works.

---

### Post by confused57 on 2007-03-02
I may have missed it reading through your thread, but if someone hasn't already suggested it, you could use the live cd to reinstall grub to hd0(your Windows drive mbr):
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Then you could add a Windows entry, similar to what has already been suggested, to your /boot/grub/menu.lst.

---

### Post by KIFIKA on 2007-03-02
sorry, i tried that and it didnt give me an error it just went back to the boot menu.

---

### Post by X-626 on 2007-03-02
Sorry, I forgot to add something to that.  I took a look at my menu.lst to try to help you.  Ty this instead:
```
title Windows XP
root (hd0,0)
savedefault
makeactive
chainloader +1
```[FONT=monospace]

and if you get that same error again, try it using rootnoverify:
[/FONT]```
title Windows XP
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1
```

---

