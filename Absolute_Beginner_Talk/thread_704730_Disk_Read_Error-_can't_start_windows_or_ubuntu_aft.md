---
title: "Disk Read Error- can't start windows or ubuntu after install"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by Papa.Gario on 2008-02-22
I installed Ubuntu yesterday morning.  It worked great, and I was really enjoying it until I tried to switch back over to windows and I started getting:

A disk read error occurred
Press Ctrl+Alt+Del to restart

Windows wouldn't start at all, but Ubunto would no problem.  So after reading around on the forums, I did what some others have and I repaired Windows... but now it goes straight to the error without giving me the chance to enter Ubuntu.

From what I understand, repairing Windows overwrites Grub, and I need to use [Super Grub Disk]("http://supergrub.forjamari.linex.org/?section=download") or [GParted]("http://gparted-livecd.tuxfamily.org/download.php") reinstall/repair it.

Is that right?  If so...

How do I do it?  The more I read on here, the more my head spins.  I've tried a couple of things already and everything I've done so far seems to either do nothing or make it worse.  I tried using Super Grub Disk from a USB, but that did nothing except get an error telling me to remove the non system disk, then I found some instructions telling me I need to use a linux disk with it, and enter in stuff at the command prompt... 

I've spent about 6 hours working on this so far, if you can help I'd really appreciate it.

---

### Post by Bruce M. on 2008-02-22
> **Papa.Gario said:**
> I installed Ubuntu yesterday morning.  It worked great, and I was really enjoying it until I tried to switch back over to windows and I started getting:

A disk read error occurred
Press Ctrl+Alt+Del to restart

Windows wouldn't start at all, but Ubunto would no problem.  So after reading around on the forums, I did what some others have and I repaired Windows... but now it goes straight to the error without giving me the chance to enter Ubuntu.

From what I understand, repairing Windows overwrites Grub, and I need to use [Super Grub Disk]("http://supergrub.forjamari.linex.org/?section=download") or [GParted]("http://gparted-livecd.tuxfamily.org/download.php") reinstall/repair it.

Is that right?  If so...

How do I do it?  The more I read on here, the more my head spins.  I've tried a couple of things already and everything I've done so far seems to either do nothing or make it worse.  I tried using Super Grub Disk from a USB, but that did nothing except get an error telling me to remove the non system disk, then I found some instructions telling me I need to use a linux disk with it, and enter in stuff at the command prompt... 

I've spent about 6 hours working on this so far, if you can help I'd really appreciate it.

Take a look at this: [Post]("http://ubuntuforums.org/showthread.php?t=210820")

Or since Ubuntu was brand new you could just install it again, as the user in the above post did.  It will install a new GRUB .

---

### Post by Papa.Gario on 2008-02-22
Thanks, I'm all out of disks at the moment -- running to wal-mart to buys some.  I'll give this a try.

---

### Post by Papa.Gario on 2008-02-22
Ok, I have the disk, and I'm trying to reinstall grub, but ... How do I do it?

That link you gave me is a little over my head -- it says to put in a command, but not where.  I know that I need to install grub from the cd, but I'm not sure how to.

Here's what he said to do:

> $> grub-install /dev/hda

Where hda is the drive you want to install grub on.

As long as the 'boot' folder in your ubuntu install is in the same place as it was (ie, hda2.. as opposed to windows making a new partition before it so it becomes hda3 etc) you should be fine, and have your grub back on reboot.

Ok... so what do I put for "hda"?  I had windows on my comp first, and then added ubuntu, so I would put hda3

edit:  if found a walk through for it, I think I might have it.  Thanks for the help.

---

### Post by Papa.Gario on 2008-02-22
AAAHHHH! 

It's still not working.  I just followed this proceder (from [here]("http://ubuntuforums.org/showthread.php?t=224351"))
[COLOR="Teal"]
When you get to the desktop open a terminal and enter. (I am going to give you the commands and then I will explain them later)

Code:

sudo grub

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)

Finally exit the grub shell
Code:

quit

That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup.[/COLOR]

Ok, so I did all that, and I'm still going straight to the "a disk read error has occurred" as soon as I power on my computer.

What am I missing?

---

### Post by Bruce M. on 2008-02-23
find /boot/grub/stage1

What was the results of that command?

---

### Post by Papa.Gario on 2008-02-23
I ended up reinstalling ubuntu completely, but I'm still having my original problem -- "disk read error" when trying to boot windows.

Give me one second and I'll tell you what it says when I type that in, I can't remember off the top of my head and PC doctor is doing a hard drive scan at the moment.

---

### Post by Papa.Gario on 2008-02-23
Ok, it returns (hd0,3)

and if this helps from sudo fdisk -l

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14991   120415176    7  HPFS/NTFS
/dev/sda2           37764       38913     9230760    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3           14992       15667     5429970   82  Linux swap / Solaris
/dev/sda4           15668       27825    97659135   83  Linux

---

### Post by Papa.Gario on 2008-02-23
The information for windows in grub is

root (hd0,0)

---

### Post by Papa.Gario on 2008-02-23
I'm looking at the system information from PC doctor and..


Drive Partition HP_RECOVERY
Drive: C
Usable Capacity:  8.79
Used Space:  8.34
File System:  FAT32

Drive Partition:  HP_PAVILION
Drive:  D
Usable Capacity:  114.84
Used Space:  45.57
File System:  NTFS

I thought C was my main drive, and D was the recovery?  Why would it show it as different now?  Did it change when I did the partition during the Ubuntu Install?

---

### Post by Bruce M. on 2008-02-23
> **Papa.Gario said:**
> Ok, it returns (hd0,3)

and if this helps from sudo fdisk -l

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14991   120415176    7  HPFS/NTFS
/dev/sda2           37764       38913     9230760    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3           14992       15667     5429970   82  Linux swap / Solaris
/dev/sda4           15668       27825    97659135   83  Linux

OK, you have one drive and sda1 is the bootable partition ( the * )

> **Papa.Gario said:**
> The information for windows in grub is

root (hd0,0)

Makes sense, Linux numbers drives & partitions from 0
So **hd0,0** is **h**ard **d**rive 1, partition 1
Linux calls that drive **sda** then numbers the partitions sda1-4

But your recovery partition is messed up:

```
/dev/sda2           37764       38913     9230760    c  W95 FAT32 (LBA)
**Partition 2 does not end on cylinder boundary.**

```

> **Papa.Gario said:**
> I'm looking at the system information from PC doctor and..


Drive Partition HP_RECOVERY
Drive: C
Usable Capacity:  8.79
Used Space:  8.34
File System:  FAT32

Drive Partition:  HP_PAVILION
Drive:  D
Usable Capacity:  114.84
Used Space:  45.57
File System:  NTFS

I thought C was my main drive, and D was the recovery?  Why would it show it as different now?  Did it change when I did the partition during the Ubuntu Install?

Looks like the C & D were reversed for some reason.
I doubt very much that that would be something Ubuntu did.

What did PC Doctor tell you?
Use that (if you can) to change the drive letter for C & D

Change in this order:
[LIST]
[*]C to E
[*]D to C
[*]E to D
[/LIST]

---

### Post by Papa.Gario on 2008-03-01
Thanks for helping me -- I understand the labeling a little better now.

I haven't had any luck yet.  I can't change the labels with pc doctor, it only has a couple of options like system test, disk scan, etc.  After it's done the only option is clicking "ok"

I'm trying to use "SystemRescueCd" but I haave no idea what to do with it.

Other people say that using their windows xp cd to type in "fixmbr" worked for them, but I don't have the disk -- does typing that in do the same thing as the supergub cd?

---

### Post by Papa.Gario on 2008-03-01
I'm so frustrated right now.

I got a windows recovery tools cd, and no luck with that.  

gah!

---

### Post by Papa.Gario on 2008-03-01
Sorry for the triple post but I found something that I'm not sure about.

Here's what's in the boot.ini:

```
[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS



[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
```

I was reading if the partition/drive didn't match up in this it wouldn't boot -- it looks alright to me but I'm novice when it comes to this.

---

### Post by Bruce M. on 2008-03-01
> **Papa.Gario said:**
> I'm so frustrated right now.

I got a windows recovery tools cd, and no luck with that.  

gah!

But you can get one here: [BootDisk]("http://www.bootdisk.com/")

Let me know how you make out
Bruce

EDIT:  I have the DOS 6.22 5 1/4 1.2 meg disk

do that and the command is:
fdisk /mbr

---

