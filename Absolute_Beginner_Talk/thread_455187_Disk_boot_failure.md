---
title: "Disk boot failure"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by dphirschler on 2007-05-26
My first attempt at installing Ubuntu didn't work out too well.  Everything seemed to be going just fine.  I booted up the OS from the CD, browsed the web a little, and then clicked the install icon.  I chose the guided option for partitioning.  Then it all installed and told me it was finished and that I needed to reboot.  So I did.  This is the error message I got.

DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

This is my first time trying to install Ubuntu and also my first exposure to SATA harddrives.  I just built this machine and the harddrive is brand new.  What could be the problem?


Darryl

---

### Post by Dzenhax on 2007-05-26
It sounds like Grub didn't install.  There's an option to install it at the end that you may have accidentally chose no for.  If that's the case, you just need to install grub.

There are similar problems here that may help you:

[http://ubuntuforums.org/showthread.php?t=455184](http://ubuntuforums.org/showthread.php?t=455184)

See starcraft.man's comments concerning GAG here:

[http://ubuntuforums.org/showthread.php?t=455151](http://ubuntuforums.org/showthread.php?t=455151)

---

### Post by dphirschler on 2007-05-26
Typing from my Ubuntu Linux PC right now.  I booted it up from the CD and followed the instructions here [http://www.daniweb.com/blogs/entry708.html](http://www.daniweb.com/blogs/entry708.html).  I got as far as this command:

```
cd /media/linux/boot/grub/
```

And I got this error:

"bash: cd: /media/linux/boot/grub/: No such file or directory"

What now?  Keep the following in mind.  Ubuntu is the only thing installed on my harddrive.  I am very much used to browsing around my harddrive in Windows, not too familiar with doing the same in Linux.  But I did try to browse to that directory and I did find /media/linux which was empty.  Do I just need tocreate the subdirectories or is the fact that it is currently empty indicate an incomplete install?


Darryl

---

### Post by Dzenhax on 2007-05-26
Ok,

     Not having done this myself I'm guessing.  But here's what I can tell you.

1. There should be two filesystems.  One is the one in memory for the live cd one is in the mount point you created in media.  That one is the hard drive.  You can navigate both with the computer choice on the places menu.

2. If you never installed grub then the directory certainly won't exist.  Try copying the contents of the Grub folder from the live CD to the hard drive and then edit it as the tutorial says.  It may take some playing with.

And if that doesn't work you can always try one of the other suggestions posted earlier.

---

### Post by confused57 on 2007-05-26
> **dphirschler said:**
> Typing from my Ubuntu Linux PC right now.  I booted it up from the CD and followed the instructions here [http://www.daniweb.com/blogs/entry708.html](http://www.daniweb.com/blogs/entry708.html).  I got as far as this command:

```
cd /media/linux/boot/grub/
```

And I got this error:

"bash: cd: /media/linux/boot/grub/: No such file or directory"

What now?  Keep the following in mind.  Ubuntu is the only thing installed on my harddrive.  I am very much used to browsing around my harddrive in Windows, not too familiar with doing the same in Linux.  But I did try to browse to that directory and I did find /media/linux which was empty.  Do I just need tocreate the subdirectories or is the fact that it is currently empty indicate an incomplete install?


Darryl
This method has worked well for me when I need to mount Linux from the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

Here's some more info on "Hard Disk" error:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#GRUB_hard_disk_error](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#GRUB_hard_disk_error)

You might want to go into  bios setup and see how it recognizes your hard drive.

---

### Post by Dzenhax on 2007-05-26
Hey DP, let us know how this is comming.  We all want it to work.

---

### Post by dphirschler on 2007-05-26
I really want this to work too.  There is just too much I like about Linux to not have a good working Linux system at home.  I am familiar with Unix to some extent.  I used to use it at work for about 8 months and we still have it at my school where I maintain my webpage.  But I never set up a Linux system from scratch before.  And I don't understand how to jump from hdd to hdd.  In DOS it's just a matter of typing c: or d:.

Give me a little time to try out some more things and I'll report back soon.


Darryl

---

### Post by dphirschler on 2007-05-26
OK, first of all, this is what I get then I do an fdisk -lu

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   384660359   192330148+  83  Linux
/dev/sda2       384660360   390716864     3028252+   5  Extended
/dev/sda5       384660423   390716864     3028221   82  Linux swap / Solaris

```
So I am guessing that this line in fstab needs to change:
```
/dev/hdb2 /media/linux /ext3
```
So do I change it to 'sda2' instead of 'hdb2'?  Does 'sda' mean it's a SATA drive?


Darryl

---

### Post by dphirschler on 2007-05-26
There are a few basic things that I need to get straight.  This might all stem from my limited understanding of SATA harddrives.  At this point, I have my PC set up like so:

1. 200GB SATA hdd, connected to SATA connection #1 on the mobo

2. Sony DVDR drive (IDE) set as master and connected to IDE connection #1 on the mobo

In BIOS, the Sony DVDR drive shows up as IDE primary master.  The SATA hdd does not show up.  I cannot even find where to set up SATA drives in BIOS.  Currently, I am looking into my documentation for my mobo to see if I have it set up right.


Darryl

---

### Post by Dzenhax on 2007-05-26
Ubuntu doesn't make any distinction between sata and ide.  The s is for scsi.  For some reason Ubuntu now recognizes all drives as scsi and lists them as sda1, sda2 where it used to be hda1 and hda2.

From what I see it looks like your boot partition is on sda1, where it should be.

Here's something else I found, try it.  It's written exactly for your situation.

Reinstall GRUB

   1. Boot from the Live CD if you can't boot from the hard disk into Ubuntu.
   2. In the terminal, run:

      sudo grub

      At the grub command prompt, run the following commands:
         1.

            find /boot/grub/stage1

            You should see something like (hdX,Y) where X and Y will be numbers, e.g., (hd0, 1).
         2.

            root (hdX,Y)

            where X and Y above should be replaced by the appropriate numbers returned in step 1.
         3.

            setup (hdX)

            where X above should be replaced by the appropriate number returned in step 1.
         4.

            quit

   3. GRUB should now be installed on the Master Boot Record (MBR). Reboot.

It has lots of other fixes that you'll need once you get the whole thing set up.  Here's the link:

[http://www.cs.cornell.edu/~djm/ubuntu/#multimedia](http://www.cs.cornell.edu/~djm/ubuntu/#multimedia)

Hope this one gets it.

---

### Post by dphirschler on 2007-05-26
OK, I just did the above steps and everything worked as planned except it still won't boot from the hdd.  Here is exactly what I see:

NVIDIA Boot Agent, PXE-2.0 (build 02 V1.82)
Copyright (C) 2001 NVIDIA Corporation
Copyright 1997-2000 Intel Corporation

CLIENT MAC ADDR: 00 0C 76 B5 34 83  GUID: FFFFFFFF-FFFF-FFFF-FFFF-FFFFFFFFFFFF
PXE-E53: No boot filename received

PXE-M0F: Exiting NVIDIA Boot Agent.
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

---

### Post by dphirschler on 2007-05-26
SUCCESS!

I knew the solution was going to be something simple.  I am almost embarrassed to admit what the problem was.  As the PC was booting, it displays all kinds of information on the screen.  It scrolls by pretty quickly.  At one point, it said there was no RAID array defined.  I'd been ignoring that message since I only have one harddrive, but apparently, I had to press CTRL+F to define a RAID array.  So I defined an array using the 'auto' setting and all was well after that.  Good grief!

Thanks for everyone's help.  I really appreciate it.  It wasn't even Linux's fault!


Darryl

---

### Post by Lucifiel on 2007-05-26
Erm, you should never install RAID unless you're really experienced with hard disks. From what I recall, Raid is only used if you've 2 SATA hdds connected together and if they're of the same hdd speed. However, RAID can cause your entire o/s to go corrupt and hdds which're enabled with Raid often tend to die faster.

So, be warned.

---

### Post by dphirschler on 2007-05-26
I had no intention of installing RAID, but apparently, I had to set up a RAID profile anyway, telling it I only had one hdd and not to make an array.  Never had to do that before, but then again this is my first experience with SATA.


Darryl

---

### Post by Dzenhax on 2007-05-26
Glad you got it working, but watch that message you posted earlier about the PXE boot.  If your bios is set to boot PXE, then it goes onto the network to look for an OS.  

Congrats,

---

### Post by dphirschler on 2007-05-26
I didn't think I had it set to boot from network, but I will definitely check that and disable it if it is set.  Thanks for the heads up.


Darryl

---

