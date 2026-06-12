---
title: "reinstalling OSX"
date: 2010-08-21
forum: Apple Hardware Users
---

### Post by Antlers on 2010-08-21
I Recently installed Ubuntu Power PC 10.04 on my ibook G4.  When I did it completely reformatted the hard drive.  Now, the mac install cd will not run when I insert it, so I cannot install OSX Panther.  When I try to use the mac install disk I  get as far as the Apple logo, where it freezes.  What can I do?  Any help is much appreciated, I have not found asolution on the forums yet.

---

### Post by JuliaKhanam on 2010-08-21
1) You can't install Windows on a G4. It has a PowerPC G4 processor  (made by Apple, IBM, and Motorola) and Windows only runs on x86  processors (made by Intel and AMD).

2) Your Linux CDs are probably also are x86 so they won't work. You can  however get a PowerPC version of Linux. Using that, yes you can install  the OS without OS X on there. Just hold option as the computer boots up  and choose to boot off of the CD. Then, follow the instructions. Just be  aware that there probably isn't as much stuff compiled for PowerPC as  for x86, especially since Apple switched to using x86 processors 4

---

### Post by Antlers on 2010-08-21
Perhaps I was  confusing.  I successfully installed Ubuntu Power PC 10.04 on my ibook g4.  Now I would like to switch back to OS Panther, but the Panther install CD will no longer load.

---

### Post by Antlers on 2010-08-21
Here is my output of fdisk -l

```
/dev/hda
        #                    type name                  length   base      ( size )  system
/dev/hda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap untitled                2048 @ 2048      (  1.0M)  NewWorld bootblock
/dev/hda3         Apple_UNIX_SVR2 untitled            30358754 @ 4096      ( 14.5G)  Linux native
/dev/hda4         Apple_UNIX_SVR2 swap                 4503552 @ 112705536 (  2.1G)  Linux swap
/dev/hda5               Apple_HFS untitled             4176900 @ 30362850  (  2.0G)  HFS
/dev/hda6              Apple_Free Extra                   1984 @ 64        (992.0k)  Free space
/dev/hda7              Apple_Free Extra               78165786 @ 34539750  ( 37.3G)  Free space
/dev/hda8              Apple_Free Extra                   1152 @ 117209088 (576.0k)  Free space

Block size=512, Number of Blocks=117210240
DeviceType=0x0, DeviceId=0x0

```

---

### Post by MacPenguin1972 on 2010-08-21
Hello Antlers,

I hear ya loud and clear. I am running a Power Mac G4 Dual Processory 1.0GHZ Desktop (the silver mirror door desktop) - I don't know if this helps or not but I am learning to, so bear with me. This is based on what I have done- I hope it will be of use.

First if you haven't done so already, copy any files from your iBook that you want to keep.

Wipe your hard drive using your Mac OS X Install Disc. While booting into that disc use DISK UTILITY (in the menus) to PARTITION your hard drive. 

Don't know what you have for hard disk space? I have two hard drives- an 80GB "master" and a 300GB "slave". I assume you have the one hard drive?   If you have the luxury of giving Ubuntu 30-40GB? I did just so I could have a lot of space for files.

Your partition for linux should be formatted as "FREE SPACE" under the Disk Utility and your other partition for Mac OS X. Install your Mac OS X then reboot your machine. 

Once you're in Mac OS X on your hard drive put in your Ubuntu install CD. Reboot the system- as SOON as you hear the Mac's "boot chime" hold down the "C" key to boot into your Linux CD. 

Ubuntu will give you the option to install into that FREE SPACE you create on Disk Utility.

Once you have done this- and you reboot, hold down the option key to give you a menu to choose between Mac OS X and Ubuntu. 

I had some troubles doing this but I finally got it. 

I'm no expert at this at all but this worked for me. I hope this will be somewhat helpful. :-)

NOW I gotta figure out how to get my @#$! permissions set so I can back up my Linux system as it is to a @#$! DVD! lol!

Enjoy!

MacPenguin

---

### Post by Antlers on 2010-08-21
I really appreciate your help.  Unfortunately I cannot boot my mac cd at all.  I get the apple logo, but not menu.  I am wondering if I need to repartition my harddrive?  Or if I make an hfs partition and copy and paste some files from the install cd into that?  I am really clutching at straws here.  Any ideas on what i can do so I can boot from the cd, or otherwise install Mac OS?  Thanks!

---

### Post by MacPenguin1972 on 2010-08-21
> **Antlers said:**
> I really appreciate your help.  Unfortunately I cannot boot my mac cd at all.  I get the apple logo, but not menu.  I am wondering if I need to repartition my harddrive?  Or if I make an hfs partition and copy and paste some files from the install cd into that?  I am really clutching at straws here.  Any ideas on what i can do so I can boot from the cd, or otherwise install Mac OS?  Thanks!

Are you holding down the C key as soon as you power on your computer with the CD in the drive?

Boot your computer with the Mac OS X CD in the drive- be sure to hold down the C key as soon as you power it on.

If nothing else put in your linux CD and see if it will let you format the hard drive. 

Either way, once you successfully launch the Mac OS X CD go into Disk Utility (found int he menus) and partition the hard disk- this will format it as well. One partition should be Mac OS X and the other (your linux partition) as "Free Space". Then reinstall your Mac OS using the partition you created for it. 

I ran into a similar problem, this fixed it for me.

hope this helps! :-)

---

### Post by Antlers on 2010-08-21
Unfortunately, my problem is running the Mac CD at all.  I can not get to the menu, yet along the disc partitions.  I do appreciate your help though.

---

### Post by Antlers on 2010-08-25
Solved.  I feel a little sheepish, I just had a bad install disk, everything's fine.

---

