---
title: "GRUB Error 17, Cannot Access any OSes"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Zorko on 2007-04-21
Right, here is my situation:
My PC has 4 hard drives in it.
1 80GB IDE hard drive (C, and V in windows XP)
2 160GB SATA drives
1 80GB SATA drive, bought specially for linux.
I have 3  OSes, Windows XP, and windows Vista, both on seperate partitions on my 80GB (C and V respecitvely) The 2 160GB drives are for data storage. The 80GB SATA has Ubuntu sat on it. I cannot boot into any OS.

I ran the install, selecting all the default options, except to install ubuntu to the 80GB drive. I rebooted, and was greeted with an Error 17 from GRUB. A quick google search tells me this means GRUB can't find my OS, or somesuch. I ran the install, and the only thing I changed from default was my keyboard layout (to UK) my time to london, and for it to install to the new 80GB drive (Selecting Guided - SCSI4 (0,0,0)(sdc) - 80.0 GB ATA SAMSUNG HD080HJ
How do I fix this? (I seem to have access to all my drives via the boot CD)

I figure from reading another thread like this I should post my menu.lst, so here it is:

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
# kopt=root=UUID=698ad264-85a1-43b1-9da4-b698bec0d3f0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,0)

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=698ad264-85a1-43b1-9da4-b698bec0d3f0 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=698ad264-85a1-43b1-9da4-b698bec0d3f0 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd3,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```

---

### Post by bulldog on 2007-04-21
It's depending on which hdd GRUB is installed,should be the IDE hdd by default.
Can you tell me which disk is your default boot device and is GRUB on this hdd?

You stated XP and Vista are on the same hdd in different partitions,but menu.lst thinks otherwise,did you modify it yourself?

Can you give the output of the command```
sudo fdisk -l
``` it's a lowercase L.
You can perform this command in a live cd session.

---

### Post by Zorko on 2007-04-21
> **bulldog said:**
> It's depending on which hdd GRUB is installed,should be the IDE hdd by default.
Can you tell me which disk is your default boot device and is GRUB on this hdd?

You stated XP and Vista are on the same hdd in different partitions,but menu.lst thinks otherwise,did you modify it yourself?

Can you give the output of the command[sudo fdisk -l[/code] it's a lowercase L.
You can perform this command in a live cd session.

Ok, GRUB is installed on the same drive ubuntu is as far as I can tell, at least the boot thing appears in the same place as all the other ubuntu stuff is. Output for sudo fdisk -l is as follows:
```
Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot Start End Blocks Id System
/dev/hda1 * 1 6095 48958056 7 HPFS/NTFS
/dev/hda2 6096 9964 31077742+ 7 HPFS/NTFS

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot Start End Blocks Id System
/dev/sda1 2 19457 156280320 f W95 Ext'd (LBA)
/dev/sda5 2 19457 156280288+ 7 HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
16 heads, 63 sectors/track, 310101 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot Start End Blocks Id System
/dev/sdb1 * 1 310099 156289864+ 7 HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot Start End Blocks Id System
/dev/sdc1 * 1 9327 74919096 83 Linux
/dev/sdc2 9328 9729 3229065 5 Extended
/dev/sdc5 9328 9729 3229033+ 82 Linux swap / Solaris
```

---

### Post by bulldog on 2007-04-21
GRUB is installed on (hd0) by default.
From my knowledge this should be the IDE hdd,not a Sata hdd,unless you changed it.
That's why I ask.

It's very important to know which disk has GRUB in the MBR,and you stated you see the GRUB menu,so you should know which hdd was set to boot.

We can reinstall GRUB onto the hdd which has ubuntu,this is a minor thing with the live cd.
**But you have to set this hdd as the default boot device in your BIOS** otherwise it won't work.

And how about the modifications in menu.lst? and vista and xp on different hdd's instead of partitions?
As far as I can see there's a windows on hda1 and sdb1,can you confirm this.
Ubuntu is located on the sdc.

---

### Post by Zorko on 2007-04-21
> **bulldog said:**
> GRUB is installed on (hd0) by default.
From my knowledge this should be the IDE hdd,not a Sata hdd,unless you changed it.
That's why I ask.

It's very important to know which disk has GRUB in the MBR,and you stated you see the GRUB menu,so you should know which hdd was set to boot.

We can reinstall GRUB onto the hdd which has ubuntu,this is a minor thing with the live cd.
**But you have to set this hdd as the default boot device in your BIOS** otherwise it won't work.

And how about the modifications in menu.lst? and vista and xp on different hdd's instead of partitions?
As far as I can see there's a windows on hda1 and sdb1,can you confirm this.
Ubuntu is located on the sdc.

This is bizarre. According to GParted HDA (the IDE drive) is split in 2. One which is 30gb and contains Vista, and the other which is 46gb and contains my XP install. This I am sure is right. I have not edited menu.lst. Grub is already installed on the same drive as Ubuntu, I can see a folder called boot along with lots of folders with names like bin, and dev, and etc. sdb is the drive I use for games, within windows, and contains no system data for any system, as far as I can tell.

EDIT: I found another folder on disk-1, the IDE drive, called Boot (note the capital B) but I think this may well be the Vista bootloader, used to switch between XP and Vista.

---

### Post by bulldog on 2007-04-21
Yes you can see the boot folder,but that's not the same as GRUB.
This is written to the MBR of any hdd,not necesarely the ubuntu hdd.
 It can be written on hda and pointing to sdc so I need to know which hdd is your boot device,otherwise I can't help you.

Or we reinstall GRUB to the sdc,then we're certain were it is :) and take it from there.
But as stated before,you need to make the hdd which has GRUB in the MBR the master boot device in your BIOS.

---

### Post by Zorko on 2007-04-21
> **bulldog said:**
> Yes you can see the boot folder,but that's not the same as GRUB.
This is written to the MBR of any hdd,not necesarely the ubuntu hdd.
 It can be written on hda and pointing to sdc so I need to know which hdd is your boot device,otherwise I can't help you.

Or we reinstall GRUB to the sdc,then we're certain were it is :) and take it from there.
But as stated before,you need to make the hdd which has GRUB in the MBR the master boot device in your BIOS.

I have confirmed that the sdc is my boot drive. I have also found out that I cannot change the order of these drives. I also remembered an advanced option during the install, about where to install the boot loader. It was set to hd0, which I left it at.

---

### Post by bulldog on 2007-04-21
Hmmm,I won't be annoying or so,but what you stated can't be true.
Unless you disconnected your other hdd's during install :) 

Grub install is (hd0) by default which can't be the sdc,because menu.lst points to (hd3,0) and when grub was installed on the sdc [master boot device] it should point to (hd0,0).
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,0)

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=698ad264-85a1-43b1-9da4-b698bec0d3f0 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=698ad264-85a1-43b1-9da4-b698bec0d3f0 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd3,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1
```

Vista however is pointing to the (hd0,0) is installed on the IDE hdd,so all evidence tells me grub is on the IDE hdd (hd0)

I know my way around with GRUB and how things should be listed,so I can't believe what you're telling me.
It's really quite simple,install GRUB on the master boot device,which hdd this should be,doesn't matter for know,however there are some things which could make live much easier :) 
From there you should be able to boot into ubuntu,perform some commands in the terminal,and we can make some entries in the menu.lst to boot vista and xp.

---

### Post by Zorko on 2007-04-21
> **bulldog said:**
> Hmmm,I won't be annoying or so,but what you stated can't be true.
Unless you disconnected your other hdd's during install :) 

Grub install is (hd0) by default which can't be the sdc,because menu.lst points to (hd3,0) and when grub was installed on the sdc [master boot device] it should point to (hd0,0).
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,0)

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=698ad264-85a1-43b1-9da4-b698bec0d3f0 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=698ad264-85a1-43b1-9da4-b698bec0d3f0 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd3,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1
```

Vista however is pointing to the (hd0,0) is installed on the IDE hdd,so all evidence tells me grub is on the IDE hdd (hd0)

I know my way around with GRUB and how things should be listed,so I can't believe what you're telling me.
It's really quite simple,install GRUB on the master boot device,which hdd this should be,doesn't matter for know,however there are some things which could make live much easier :) 
From there you should be able to boot into ubuntu,perform some commands in the terminal,and we can make some entries in the menu.lst to boot vista and xp.
I am sorry, I don't quite understand. Basically the boot loader is on my boot drive, and as far as I can tell from my BIOS my boot drive is the IDE drive. So what you are saying is correct (As far as I understand :confused: ) So how do I install GRUB to that drive?

---

### Post by bulldog on 2007-04-21
To make things much simpler reinstall grub.
Follow the next commands with care and look if there's an error.
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next command 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

The setup (hd0) command should be changed.
Use the number which you'll get with the find command,so when  the find command gives back (hd3,0) use setup (hd3) instead!!

---

### Post by Zorko on 2007-04-21
> **bulldog said:**
> To make things much simpler reinstall grub.
Follow the next commands with care and look if there's an error.
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next command 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

The setup (hd0) command should be changed.
Use the number which you'll get with the find command,so when  the find command gives back (hd3,0) use setup (hd3) instead!!

I have just done this, with no errors. I shall try a reboot.

---

### Post by bulldog on 2007-04-21
You should boot from the sdc hdd otherwise it will not have any effect!!
If you let it boot from the hda your problem persist,because that's another GRUB in the MBR.

But let's hope for the best shall we?

**EDIT**
I'm gonna sleep for a few hours now,I'll be back tomorrow afternoon.
If it's not solved and you need help,just give me a PM and a link to this topic and I'll be back to help you out.

---

### Post by Zorko on 2007-04-21
> **bulldog said:**
> You should boot from the sdc hdd otherwise it will not have any effect!!
If you let it boot from the hda your problem persist,because that's another GRUB in the MBR.

But let's hope for the best shall we?

**EDIT**
I'm gonna sleep for a few hours now,I'll be back tomorrow afternoon.
If it's not solved and you need help,just give me a PM and a link to this topic and I'll be back to help you out.

Attempted to boot from every drive in the system, just for kicks. The hda gave me the grub error, the sdc seemed to do nothing. sda gave me a "cannot load operating system" or somesuch error, but no mention of grub. I shall try again.

---

### Post by Nightmist on 2007-04-21
I am really interested to see if you can get this to work, as I have a similar problem (on a different computer than this). But there is only one HDD on that. Currently it has 3 partitions (win98, ext3 and linux swap) on the single HD, and I still get Error 17.

I hope you get it to work so maybe I can better understand what's wrong. I mean... there is no other place to put Grub than in the MBR of hd0, and that is right when you only have 1 HD, right? So what can be wrong in my case?

Good luck!

---

### Post by Zorko on 2007-04-21
Finally booted into grub, by changing line setup (hd0) to setup (hd3)
However when i try to select any Ubuntu thing I get Error 17 (again)
When I boot the Vista bootloader I get error 13 (something about an incompatible (unrecognised) executable, and when I boot vista it gets to starting... and hangs.

EDIT: I get the feeling I am doing something monumentally stupid :(

---

### Post by Nightmist on 2007-04-21
> **Zorko said:**
> Finally booted into grub, by changing line setup (hd0) to setup (hd3)
However when i try to select any Ubuntu thing I get Error 17 (again)
When I boot the Vista bootloader I get error 13 (something about an incompatible (unrecognised) executable, and when I boot vista it gets to starting... and hangs.

EDIT: I get the feeling I am doing something monumentally stupid :(

I think you're halfway there now that you got the bootloader to start. But it seems the Live CD totally mixed up your drives or something (you got a somewhat complicated setup I guess). Maybe you should try changing where the Ubuntu entry in the Grub menu points to (is it hd3,1 or something?).

But this is a frustrating problem, since a failed Grub paralyses your whole system. Isn't there a way Grub can revert back to the previous MBR if it gets a failure, or do a test run to check if it got everything right before overwriting the existing one? I'm getting nervous when helping friends installing Ubuntu now since I can cripple their whole system if I can't set up Grub properly...

:confused:

---

### Post by Nightmist on 2007-04-21
I think I actually can answer my own question: A Grub boot floppy

[https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy)

That way you can test it with a floppy first, and restore your old one as well. I will definately try this next time. However, this is of little help to both of us at this point. Maybe this page can be of some help, though:

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by Nightmist on 2007-04-22
> **Zorko said:**
> Finally booted into grub, by changing line setup (hd0) to setup (hd3)
However when i try to select any Ubuntu thing I get Error 17 (again)
When I boot the Vista bootloader I get error 13 (something about an incompatible (unrecognised) executable, and when I boot vista it gets to starting... and hangs.

EDIT: I get the feeling I am doing something monumentally stupid :(

I'm curious... did you get it to work yet?

---

### Post by bulldog on 2007-04-22
@zorko

To begin,it's possible your Vista is borked because grub was placed in the MBR of the hdd.
Don't know if Vista has a recovery function build in,had only a play for two days with Vista,and was really bored with it,so I'll never install it again I think.
So maybe you have to reinstall Vista,can' say it otherwise.

Well you managed to get grub working,that's nice but now we have to change your menu.lst to have your ubuntu to boot.
Explanation,GRUB is now on your sdc,and when you set this hdd to boot,it will become (hd0).
In the menu.lst your ubuntu is set to start from (hd3,0),and as you can imagine,this is not good at all.
We'll have to change it to (hd0,0) to boot.
Another thing is the UUID thingy which makes your drive unique among the others,we'll have to take a look at that as well,and your /etc/fstab file,will be pointing to the wrong locations either.
But that's all to change and make it as we like.

We begin with the mounting of the ubuntu partition to set things up.
Boot into a live session and open a terminal.
Make a mount point,mount the partition,take a look at the UUID's [note them down please],take a look at the device.map and copy it to the forum,take a look at fstab and copy it to the forum,the menu.lst is on the forum already,so we can use that one.
Copy and paste the commands in a terminal one by one,and copy the output of the relevant commands to the forum.[UUID,device.map,fstab]
```
sudo mkdir /mnt/rescue
sudo mount /dev/sdc1 /mnt/rescue
sudo vol_id -u /dev/sdc1
cat /mnt/rescue/boot/grub/device.map
gksudo gedit /mnt/rescue/etc/fstab
```

If this is on the forum,I take a look and change them as they should be,then you copy them back and replace the menu.lst and fstab with the new one,after that you should be able to boot at least into ubuntu and in XP.
Vista I'm not sure of however.

---

### Post by bulldog on 2007-04-22
> **Nightmist said:**
> I think you're halfway there now that you got the bootloader to start. But it seems the Live CD totally mixed up your drives or something (you got a somewhat complicated setup I guess). Maybe you should try changing where the Ubuntu entry in the Grub menu points to (is it hd3,1 or something?).

But this is a frustrating problem, since a failed Grub paralyses your whole system. Isn't there a way Grub can revert back to the previous MBR if it gets a failure, or do a test run to check if it got everything right before overwriting the existing one? I'm getting nervous when helping friends installing Ubuntu now since I can cripple their whole system if I can't set up Grub properly...

:confused:

GRUB seems to be a terrifying application for some users,but it isn't.
The only thing it does is to scan were bootable OS's are installed and place them in a file called menu.lst.
There are somethings you should be aware of.
If you have multiple hdd's and you install ubuntu on a separate hdd from windows,it's best to make the hdd with ubuntu the master boot device and install GRUB in the MBR of this hdd.
You can boot windows,with a minor modification that is,and ubuntu from the GRUB menu,**but when there's something bad happened with GRUB,you can always boot your windows from it's own boot loader,by setting the windows hdd as the master boot device**

That's why it's important to know which hdd is the master boot device,and correct it if necessary,** before you install ubuntu** so GRUB will be on the correct location from the beginning.
That makes life much easier.
A second benefit of this manner is,you can reinstall windows without loosing the GRUB menu,because it's on another hdd.

With Edgy and Feisty,partitions are named with a so called UUID,which makes them unique in the configuration,so we have to see in fstab and menu.lst,if they are correctly listed,as I see it goes wrong with the UUID several times now.
Can't give an answer why it goes wrong,but it does,maybe through some interference of a user,or maybe something else.

But If you have the hang of how things are done with GRUB,it isn't difficult at all,you only have to make sure the partition's have the same correct UUID or device name,otherwise your boot will hang or whatever.

---

### Post by Nightmist on 2007-04-22
I can understand that Grub can be confused when you have more than one HD. I got Error 17 on a PC with only one HD, though. It has windows 98 on hda1 and Linux and swap on hda2 and hda3.

I did the sudo grub thing with setup (hdo) and all that jazz. I could only get successful install on (hd0,1) which looks right. But when I boot up, I get Error 17.

I got a Windows 98 boot disk so I could do fdisk /mbr to restore the system, so I can always boot to Windows when I need to use the computer. But that one sets me back to where I started.

I guess my question is... how can Grub NOT find itself when I have one HD, Linux installed on hda2, and the Grub setup pointing to (hd0,1) ?

---

### Post by bulldog on 2007-04-22
If you can give me the output of```
sudo fdisk -l
``` and a copy of the menu.lst and the fstab as well, I certainly will have a look at it.
Which ubuntu do you have?Feisty,Edgy or Dapper?

EDIT,Never mind,I see you use Dapper in your profile.

---

### Post by Nightmist on 2007-04-22
> **bulldog said:**
> If you can give me the output of```
sudo fdisk -l
``` and a copy of the menu.lst and the fstab as well, I certainly will have a look at it.
Which ubuntu do you have?Feisty,Edgy or Dapper?

EDIT,Never mind,I see you use Dapper in your profile.

The version in my profile is not related to the PC I'm struggling with. At home my Kubuntu is shiny and nice. On the one with the Grub problem, I started with Dapper Drake, then Edgy Eft (Xubuntu for that one) and just now Feisty Fawn. All gave the same result.

The PC I am trying to fix doesn't have an internet connection, but I'll try to write down the important parts at a later date. I gave up for today after trying for a few hours.

---

