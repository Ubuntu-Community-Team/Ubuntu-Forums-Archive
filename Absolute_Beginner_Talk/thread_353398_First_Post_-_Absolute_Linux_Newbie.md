---
title: "First Post - Absolute Linux Newbie"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by Wreckless Randy on 2007-02-04
Hello Everyone, my name is Randy, and I'm an absolute newbie
to both Ubuntu and Linux.

In fact, I haven't even got my Ubuntu CD yet.  I ordered the free
6.06LTS version, and I figure I will have plenty of time to learn, learn,
learn and prepare myself before it arrives.

I have been eyeing Linux for quite some time now, but have been
waiting to begin my gradual migration from windows until NTFS support
improved.  Well, the newly released Windows Vista gave me a nudge
to look at Linux again (it was designed in part by the NSA - this puts
my hackles up).  It appears that with ntfs-3g, Linux is now at least
initially NTFS read/write friendly.  So here I am. ):P 

It appears that this forum is pretty darn friendly to ignorant newbies
like myself, so I guess I'll begin with my initial questions.  Please be
kind, and know that I have been reading a lot, but I won't entirely
get my head wrapped around Linux until I actually start working
hands-on with it.  I don't mind looking further information up if
you'll just help point me in the right direction.  As with anything new,
it is a bit overwhelming when I look up a topic and there seems to
be as many different answers as there are individuals.  So...

**1)**I'm a bit confused about the **6.06LTS CD** - **is this a "live" version**?

**2)**I want to try "live" first if possible, but then when I do install, I
will want a dual boot with my Windows XP.  (please don't tell me
how stupid it is to keep my XP, I've got good reasons to)  - AND -
I want ntfs-3g RIGHT FROM THE GET GO.

I think I want to use this utility [http://givre.cabspace.com/ntfs-config/](http://givre.cabspace.com/ntfs-config/)
As it appears to make it easier.  But I'm a bit confused...

-**Do I need to install something called FUSE first?**
-[B]Do I need to install ntfs-3g BEFORE I use that utility?  OR does
that utility access the ntfs-3g installer for me?[/B]

**3)**[B]Is it better to install Ubuntu on the same drive partition as my XP,
or on a different partitiion or drive altogether?  How much room should
I make sure to have before I do this?[/B]

I am thinking of upgrading the size of my hard drive before my Ubuntu
arrives... [I]any tips on how best to organize things from the very beginning
in order to make things as smooth as possible[/I]?


:)  THANK YOU TO ANY AND ALL RESPONSES... I really want to get
my head around this before I install, and I appreciate greatly anyone
taking the time to help me understand how these different OS's work
together best. :)

---

### Post by Wikzo on 2007-02-04
Hey

I am a new user of Ubuntu as well, and I have never tried anything Linux before. I am "just" 15 years old, but I handled to get the 6.10 working in dual boot mode with my Windows XP.

I just want to say: If you have some time and some experience with computers, there will be no problems. Just read some guides and try it out - then you'll learn it.

To answer one of your questions:
When you get the Ubuntu cd, you have to choose the buttun "Run or install Ubuntu". Then after some time you'll end up on a deskop, that is running LIVE on your pc's ram. If you like it you can pick the icon who says "Install" and install it on your harddrive. It is really smart maded; the install cd can both run live and install the system on your machine.

Good luck with Ubuntu! :)

---

### Post by Falcorian on 2007-02-04
> **Wreckless Randy said:**
> Hello Everyone, my name is Randy, and I'm an absolute newbie to both Ubuntu and Linux.

Hi Randy, welcome to Linux. Hope you enjoy your stay!

> **Wreckless Randy said:**
> I have been eyeing Linux for quite some time now, but have been waiting to begin my gradual migration from windows until NTFS support improved.  Well, the newly released Windows Vista gave me a nudge to look at Linux again (it was designed in part by the NSA - this puts my hackles up).  It appears that with ntfs-3g, Linux is now at least initially NTFS read/write friendly.  So here I am. ):P 

I've never tried ntfs-3g, so take what I say with a grain of salt. Without it you should be able to read NTFS fine, but not to write to it. NTFS-3G adds writing, but since I've never tried, I can't judge how well.

> **Wreckless Randy said:**
> **1)**I'm a bit confused about the **6.06LTS CD** - **is this a "live" version**? 

It's a Live CD. You can pop it in and give Ubuntu a shot. The CD will also allow you to install from live mode, which is (noramlly) easy and straight forward.

> **Wreckless Randy said:**
> **2)**I want to try "live" first if possible, but then when I do install, I will want a dual boot with my Windows XP.  (please don't tell me how stupid it is to keep my XP, I've got good reasons to)  - AND - I want ntfs-3g RIGHT FROM THE GET GO.

I think I want to use this utility [http://givre.cabspace.com/ntfs-config/](http://givre.cabspace.com/ntfs-config/)
As it appears to make it easier.  But I'm a bit confused...

-**Do I need to install something called FUSE first?**
-[B]Do I need to install ntfs-3g BEFORE I use that utility?  OR does
that utility access the ntfs-3g installer for me?[/B]

I'm going to skip answering this, since I don't know, hopefully someone can help you out.

> **Wreckless Randy said:**
> **3)**[B]Is it better to install Ubuntu on the same drive partition as my XP,
or on a different partitiion or drive altogether?  How much room should
I make sure to have before I do this?[/B]

I am thinking of upgrading the size of my hard drive before my Ubuntu
arrives... [I]any tips on how best to organize things from the very beginning
in order to make things as smooth as possible[/I]?

You shouldn't have any problems installing on the same drive. The Live CD will allow you to adjust your partitions accordingly. (But WARNING: Backup data! While I haven't had a problem, move and resizing partitions is always risky!) Ubuntu will be installed on it's own partition of the drive.

I set up my dual boot (when I was still doing it) as follows:

15 gigs for windows
20 gig partition of FAT32 (both Linux and Windows and Read/Write this one, so you can share files between the two easily).
1 gig swap partition for Linux
10 gig / director for linux
10 gig /home for linux

I would really recommend having / and /home on separate partitions, that way you can reinstall Linux if need be to / , and all your data and personal files in /home will be fine.

I'm sure there's a guide for this, but I don't know where it is off the top of my head.

So, best of luck!

---

### Post by xpod on 2007-02-04
Heres a great site that should help you with some of the basics guy`s..

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

Good luck and welcome to the forums

---

### Post by Wreckless Randy on 2007-02-04
THANK YOU, THANK YOU, THANK YOU SO MUCH! :) 

All of you!  For your quick and helpful responses.
I'm going to continue reading and studying, and checking
out your info.

---

### Post by igknighted on 2007-02-04
I would not recommend using ntfs-3g if you have really important data on your windows partition.  It is still developmental and there are no guarantees as to its safety.  That said, linux can read ntfs perfectly fine and safely.  Also, there are windows drivers for ext3 (thank you open source) so you can read and write to your linux partition safely.  I would use the linux partition (or an extra ext3 shared partition) to store data you want for both.  Also, many recommend using fat32 as a shared partition.  This is an old file system which isnt terribly stable and also has a file size limit.  You cant store large files (such as dvd images) on it.

---

### Post by Falcorian on 2007-02-04
> **igknighted said:**
> I would not recommend using ntfs-3g if you have really important data on your windows partition.  It is still developmental and there are no guarantees as to its safety.  That said, linux can read ntfs perfectly fine and safely.  Also, there are windows drivers for ext3 (thank you open source) so you can read and write to your linux partition safely.  I would use the linux partition (or an extra ext3 shared partition) to store data you want for both.  Also, many recommend using fat32 as a shared partition.  This is an old file system which isnt terribly stable and also has a file size limit.  You cant store large files (such as dvd images) on it.

I'd listen to knighted. I've never tried the EXT3 support for Windows, but that would probably be the best option if the support is as good as Knighted says (again, never tried it, so I can't say).

---

### Post by msandersen on 2007-02-05
NTFS-3G is indeed an experimental Beta, maintained for Ubuntu by givré in [this thread.]("http://ubuntuforums.org/showthread.php?t=217009"). Use the detailed instructions there once Ubuntu is installed. I have had no problems with it, but since it is still experimental, updates sometimes can break things temporarily. Posts to that thread has seen the problems fixed quickly, though. So sometimes it pays to not install updates as soon as they appear, but wait a bit for others to stumble on problems which are promptly posted on these forums and hopefully quickly fixed.

On Windows XP, you should then install the [Ext2IFS driver]("http://www.fs-driver.org/") and mount whichever partitions you want to share, like Home and Data dirs (but not the Root [System] partition).

If you do upgrade to a larger driver, presumably you'll clone the disk over, and so conveniently have a complete backup. The clone tool may also provide some options of what to do with the unused space. If you have Partition Magic, or can get your hands on it, use it to partition the new drive. It is better than the GParted partition editor used by the Ubuntu install CD, which is still an early Beta (I think v0.1 on the Dapper CD). I know Linux users will cringe and argue the point. A couple of people have run into a bug in I think NTFS-Resize when using it to move a partition, making Windows unbootable (though fixable if you know how; the partition itself is OK). Personally I used the Alternative CD as I was upgrading (the main CD can't be used to upgrade), but I also used it in a fresh install, as the old text installer it uses is probably safer. 

There are many guides on installing, Cybercat's guides probably being a good one. A good rule is; 3 partitions. One Root (System) partition (no less than 3Gb for safety, 5Gb should be fine), one Home partition, and one Swap partiton (1.5 to 2 times the amount of RAM; eg I have 896Mg RAM, and a 1Gb swap. Could have made it bigger, but it does the trick).

---

### Post by Wreckless Randy on 2007-02-05
> **msandersen said:**
> If you have Partition Magic, or can get your hands on it, use it to partition the new drive. It is better than the GParted partition editor used by the Ubuntu install CD, which is still an early Beta (I think v0.1 on the Dapper CD). I know Linux users will cringe and argue the point. 

I assume you're talking about using Partition Magic after the initial install?
Or before?  Or is there some magical way to use it *during* the install?

---

### Post by msandersen on 2007-02-06
No, Partition Magic is a Windows program; when planning to install, you make the partitions beforehand from Windows (PM can make ext2/3 and swap partitions) and then when installing Ubuntu, choose those partitions for / (root), /home, and swap. At this stage I think it's somewhat safer, tried and tested etc, and of course NTFS is native to Windows, so you're liable to have less trouble moving/resizing from Windows. No guarantees though.

---

