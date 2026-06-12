---
title: "Problem dual booting windows and ubuntu (ubuntu installed 1st, windows 2nd)"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by seeknowsage on 2007-08-04
I am attempting to install Windows XP on an unused partition of a hard drive on my system. I've been running Ubuntu on this system for awhile now. However, while I know this causes problems with grub (that I believe I've prepared to deal with at a later time), I am unable to switch around the install order of the OS's. 

As it stands, I've formatted the unused partition and copied the windows files over to it for setup. When the system reboots itself and after I've removed the windows cd, nothing loads. Specifically, I am able to edit my BIOS settings, but beyond that, the system stalls after no bootable disc is found in either of my cd drives and I am presented with just a blinking cursor. 

I've attempted to change the boot order of my system devices to no avail. Does anyone have any idea how to remedy this problem?


NOTE: I'd like to continue with the windows setup if possible.

---

### Post by kyphi on 2007-08-04
> As it stands, I've formatted the unused partition and copied the windows files over to it for setup.

The usual way to install Windows is to just put the disc into the CD/DVD drive.  Just keep an eye on the installation so that it does not reformat your entire hard drive.

When you have Windows installed you will not be able to access your Ubuntu installation unti you organise a GRUB file.

It would be better if you were to use a separate hard drive for each operating system.  In case of a hard drive crash you would not be left without an operating system.

---

### Post by seeknowsage on 2007-08-04
Thanks for your reply. I am sorry for not being explicit in what I posted. )=


Anyways, here is what I have done:
1. Rebooted with Windows XP cd in cd drive
2. Booted from Windows XP cd
3. Formatted unformatted partition on hard drive
4. Allowed installation to copy windows files to the newly formatted partition
5. Rebooted
6. Said a hearty hello to the blinking cursor that keeps staring at me.

Since then, I've used Super Grub Disc to recover grub and I'm able to get back into my Ubuntu setup with no problem whatsoever. However, I still can't access the windows side to complete the windows setup or get grub to boot to that partition properly. )=

---

### Post by kyphi on 2007-08-04
> 4. Allowed installation to copy windows files to the newly formatted partition
5. Rebooted

The Windows installation takes a bit longer than what you describe.  After the files are copied to the newly formatted partition it has to install them.  If you are installing XP, the process will take about 45 minutes.  Any reboots that are deemed necessary by the automatic installer will happen automatically.

Good that you have Super Grub Disc to hand, a very handy tool indeed.

---

### Post by MQMike on 2007-08-04
Here’s a how-to where I added a post (see July 24) dealing with this:

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
(This is the basic, general Post#1)

HOW To:  Change the Default Operating System (Also:  Changing the timeout, boot menu, and other tips)
April 21, 2007

Install Windows XP *after* K/Ubuntu, and install XP to a non-first hard drive: map command
July 24, 2007

---

### Post by seeknowsage on 2007-08-04
> **kyphi said:**
> The Windows installation takes a bit longer than what you describe.  After the files are copied to the newly formatted partition it has to install them.  If you are installing XP, the process will take about 45 minutes.  Any reboots that are deemed necessary by the automatic installer will happen automatically.

Good that you have Super Grub Disc to hand, a very handy tool indeed.

Thanks again for your reply! Yeah, installing windows is always a pain in the amount of time it takes. When I tried it above, I allowed it to copy the files it needs to the drive from the cd before it decided to reboot. During the normal course of a windows installation, the cd is then removed and windows is then setup from the files copied over to the drive. 

However, I am not making it to this step. Before, I was getting the evil eye from the blinking cursor on the black screen. Normally, the windows installation would have already initiated. I waited in excess of 30 minutes for this to occur but nothing happened. Now, I am attempting to boot into that partition using grub, but now I get errors like: 

Error 23: Error while parsing number

Error 12: Invalid device requested

These errors vary depending upon where I tell grub the windows partition is at. I've tried a trial and error approach to editing the windows location in grub (hd0,0; hd0,4; etc) but this didn't help.

At this point I just want to be able to access that partition when booting so I can continue the windows installation. )=

---

### Post by kyphi on 2007-08-05
You cannot boot to the XP partition because it is not yet a bootable operating system.  It has been some time since I have had to install (reinstall) XP but I do not recall taking the disc out for a reboot.

What happens if you leave the disc in the drive when you reboot?

There might be some information on that on the Microsoft site.

The dual boot system that I have uses two hard drives, one for each operating system.

---

### Post by kirios on 2007-08-05
[COLOR="DarkRed"]Is your XP partition at the beginning of the disk? 
XP doesn't boot unless it's on the first primary partition (/dev/hda1). [/COLOR]

---

### Post by runesvend on 2007-09-25
> **seeknowsage said:**
> 
Anyways, here is what I have done:
1. Rebooted with Windows XP cd in cd drive
2. Booted from Windows XP cd
3. Formatted unformatted partition on hard drive
4. Allowed installation to copy windows files to the newly formatted partition
5. Rebooted
6. Said a hearty hello to the blinking cursor that keeps staring at me.

I'm experiencing this exact same thing. I have already installed Ubuntu on my hard drive called /dev/sda and I've tried installing Windows XP on /dev/hda on the partition hda2 (the first partition on hda, hda1, is filled with data so I'm installing on the second partiton on that hard drive).

Does anyone know what to do? First half of the XP installations goes fine but when the Windows installation reboots my computer it doesn't continue to the second half of the installation.

I can see XP has put two files called boot.ini and bootex.log on partiton hda1, and a WINDOWS folder and PAGEFILE.SYS file on hda2.

Any input is appreciated!

---

### Post by shirilover on 2007-09-25
You may want to try adding something similar to the following in /boot/grub/menu.lst
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Though, it may be necessary to change the root line.

---

### Post by runesvend on 2007-09-26
I've tried putting these four options in my menu.lst file:

> title		Microsoft Windows XP Professional 1
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Microsoft Windows XP Professional 2
root		(hd0,1)
savedefault
makeactive
chainloader	+1

title		Microsoft Windows XP Professional 1 (noverify)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

title		Microsoft Windows XP Professional 2 (noverify)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

Neither of them works. When choosing the ones trying to boot from (hd0,0) it says "Starting up ..." and hangs there. When choosing the ones trying to boot from (hd0,1) it says:

> Starting up ...

Remove disks or other media
Press any key to continue

Any ideas?

---

### Post by runesvend on 2007-09-29
*bump*

I would really like this to work... anyone?

---

### Post by kirios on 2007-09-30
[COLOR="DarkRed"]Please post /etc/fstab and the output of fdisk -l.[/COLOR]

---

### Post by runesvend on 2007-09-30
The content of /etc/fstab is as follows:

> # /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda1 :
UUID=0EBB5AFE231306A9 /media/hda1 ntfs-3g defaults,force,locale=en_US.UTF-8 0 1
# Entry for /dev/sda3 :
UUID=1A780D1B780CF773 /media/sda3 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda4 :
/dev/sda4 /media/sda4 ext3 defaults 0 1
# Entry for /dev/hda3 :
/dev/mapper/cswap none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/cdrom /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0

*fdisk -l* gives me no output...

---

### Post by meierfra on 2007-09-30
You need to use sudo with fdisk:

```
sudo fdisk -l 
```
(l  is a lower case L)

---

### Post by runesvend on 2007-09-30
That did the trick! Here's the output:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           60541       60801     2096482+  82  Linux swap / Solaris
/dev/sda2           55841       60540    37752750   83  Linux
/dev/sda3               1        9791    78646176   83  Linux
/dev/sda4            9792       55840   369888592+  83  Linux

Partition table entries are not in disk order

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       19146   153790213+   7  HPFS/NTFS
/dev/hda2   *       19147       19929     6289447+   c  W95 FAT32 (LBA)
```

---

### Post by meierfra on 2007-09-30
According to your fdisk Windows seems to be on first partition of the second hard drive. 
Try

> 
title Microsoft Windows XP Professional 2
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1



If this does not work post the output of

cat /boot/grub/device.map

and 

cat /boot/grub/menu.lst

---

### Post by kirios on 2007-09-30
> **runesvend said:**
> 
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       19146   153790213+   7  HPFS/NTFS
/dev/hda2   *       19147       19929     6289447+   c  W95 FAT32 (LBA)[/CODE] 
[COLOR="Red"]You seem to have installed Windows  on the **second** partition of the second disk (hd1,1) (as you also mentioned in your first post).[/COLOR] 

> **runesvend said:**
> I have already installed Ubuntu on my hard drive called /dev/sda and I've tried installing Windows XP on /dev/hda on the partition hda2 (the first partition on hda, hda1, is filled with data so I'm installing on the second partiton on that hard drive)... 
I can see XP has put two files called boot.ini and bootex.log on partiton hda1, and a WINDOWS folder and PAGEFILE.SYS file on hda2.
[COLOR="Red"]As far as I know, XP won't boot unless it's on the first primary partition of the first disk, in which case mapping may not help. 

Adding **hide (hd1,0)** to your menu.lst entry for Windows probably won't work either as boot.ini seems to be on hda1. 

I would suggest reinstalling on (hd0,0) which is currently sda3 (by the way, where is your / partition?!) 

Windows will overwrite the MBR, so you'll then need to reinstall grub by running the Ubuntu live CD/DVD.[/COLOR]

---

### Post by runesvend on 2007-10-06
OK, thanks for the advice.

I should note that what you call (hd0) (sda) is connected to my computer via a SATA controller card (I only have IDE connectors in my computer as it's 4-5 years old so I had to buy a SATA controller).

But why do you say that *sda* the 'first' disk? Because fdisk listed in first in its response to the *fdisk -l* command? I'd rather not move anything around on sda as it's pretty crowded (as you can see from the fdisk outout). I have a lot of data on sda3 that I would like to keep separated from Windows. Is there any reason why Windows wouldn't boot from the **first** partition on *hda* if I were to install it on this? This disk is connected to the first IDE channel on my motherboard. Right now I boot Ubuntu from a floppy, I'm not sure I can boot it from the *sda*-disk since it's connected the way it is.

EDIT: I just found out that GRUB calls *hda* (hd0) and *sda* (hd1). Take a look at this command outout:

```
grub> find /boot/grub/stage1
 (fd0)
 (hd1,1)
```

The (hd1,1) is the location of my Ubuntu isntallation, (on sda2).

---

### Post by kirios on 2007-10-06
[COLOR="Red"]In that case, backup hda1, delete both partitions (hda1, hda2) and reinstall Windows on hda (use Windows Setup to partition and format the disk during install). 

Windows will overwrite the MBR but you'll still be able to boot Ubuntu from the floppy disk.[/COLOR]

---

### Post by runesvend on 2007-10-07
Cool, thanks a lot! I will do that. I will basically just back up the hda1 partition, delete both partitions present on the disk, make a new ~6 GB FAT32 partition at the beginning of hda (which will hold Windows) and create an NTFS partition following the FAT32 one which will hold the backed up hda1.

Do you know of any other partition backup utilities besides *partimage* for Ubuntu? I'm a bit wary when it comes to its 'experimental' support of NTFS.

---

### Post by kirios on 2007-10-07
> **runesvend said:**
> Cool, thanks a lot! I will do that. I will basically just back up the hda1 partition, delete both partitions present on the disk, make a new ~6 GB FAT32 partition at the beginning of hda (which will hold Windows) and create an NTFS partition following the FAT32 one which will hold the backed up hda1. 
[COLOR="DarkRed"]Windows XP will need more than 6 GB when you factor in the system folder, program files, paging file and the fact that Disk Defragmenter needs at least 15% of empty disk space to run. 

I would suggest using ntfs for the Windows system partition (hda1)and fat32 for the data partition (hda2). [/COLOR]

> **runesvend said:**
> Do you know of any other partition backup utilities besides *partimage* for Ubuntu? I'm a bit wary when it comes to its 'experimental' support of NTFS. 
[COLOR="DarkRed"]If hda1 has only data files at the moment, you could use **cp -R** to copy the files and folders recursively to an external hard disk or USB flash drive. Imaging utilities are generally for backing up a system partition.[/COLOR]

---

### Post by dabar12 on 2008-01-25
I'm having a simular problem,

I have Ubuntu 7.10 installed in sda2 (ext3) into a 9gig partition which was an attempt to not affect the first portion of the disk I had WindowsXP already installed in (which was virused)..I probably overlapped that windowsXP partition which doesn't give me a good feeling about files I was trying to keep (that free space outside, or before of ubunto became unallocated). I installed another version of windows XP over which ended up being /dev/sda1 into 30gigs of space, (there's 50gigs unallocated in the middle of the two).

I followed everything here except after the "find /boot/grub/stage1" returned "(hd0,1). I still had to run "setup (hd0)" because trying to do "setup (hd0,1)" would tell me it failed, I'm not clear all the way as to what I'm doing. Also when I went to boot up Ubuntu, on the menu it was trying to boot "(hd0,2)" So I changed those in the menu.lst and did some experimenting of what "hd" to try to get windows to run under and nothing's worked to get windows to boot up correctly off the list. Any help would be greatly appreciated

---

### Post by dabar12 on 2008-01-25
> **kirios said:**
> [COLOR="Red"]You seem to have installed Windows  on the **second** partition of the second disk (hd1,1) (as you also mentioned in your first post).[/COLOR] 


[COLOR="Red"]As far as I know, XP won't boot unless it's on the first primary partition of the first disk, in which case mapping may not help. 

Adding **hide (hd1,0)** to your menu.lst entry for Windows probably won't work either as boot.ini seems to be on hda1. 

I would suggest reinstalling on (hd0,0) which is currently sda3 (by the way, where is your / partition?!) 

Windows will overwrite the MBR, so you'll then need to reinstall grub by running the Ubuntu live CD/DVD.[/COLOR]

I'm looking for a reply before I mess things up by trying to install XP again in that first partition of my one hard drive [would that be (hd1,0)?] , I'm not concerned with backing up XP, nothing on it. I want to know why he should reinstall GRUB from the Ubuntu live CD, because it's from another HD? I've run the "setup (hd0)" command and want to know if it's all the same.

I was going by [this dualboot guide]("http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp")

here's a couple outputs I have so you guys can know what's going on:

```
root@dabar-laptop:/etc# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=4b10937c-b494-4963-ba98-fcef47608d35 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=45a2cd55-86b3-4a69-a62e-40e5bc96b22f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

I also wanted to understand the "(hd0), (hd1,0)" displays and how to find out which device is what under those displays

```
root@dabar-laptop:/home/dabar# sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06ce06ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2           10515       11789    10241437+  83  Linux
/dev/sda3           11790       12050     2096482+  82  Linux swap / Solaris
root@dabar-laptop:/home/dabar# 

```

I hope I'm not just dropping my whole deal in the middle of a thread, I believe I'd read others well enough and want to know were to go from here basically....also

```
root@dabar-laptop:/home/dabar# cat /boot/grub/device.map
(hd0)   /dev/sda
```

I think I almost answered part of my own question right there, I'm trying to figure what manpages to read too. thanks in advance

---

