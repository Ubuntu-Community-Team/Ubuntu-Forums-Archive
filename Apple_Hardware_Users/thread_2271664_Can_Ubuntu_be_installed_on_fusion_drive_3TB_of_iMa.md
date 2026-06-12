---
title: "Can Ubuntu be installed on fusion drive 3TB of iMac 27 inch 5K retina (early 2015)"
date: 2015-03-31
forum: Apple Hardware Users
---

### Post by mohamed15 on 2015-03-31
I wish to know if anyone tried to install ubuntu along with OS X. The core question is how to install ubuntu on fusion drive (3TB). I need a tested and working way. The only solution I found is to install ubuntu on external hard disk. I have not tried this. If there is a way, kindly show it in a simple way to someone like me who is new at all to command line. 

Thanks in advance,
Mohamed

---

### Post by mohamed15 on 2015-03-31
I forget to mention that I already installed windows 8.1 with Yosemite 10.10.2 using bootcamp.

---

### Post by este.el.paz on 2015-04-03
> **mohamed15 said:**
> I forget to mention that I already installed windows 8.1 with Yosemite 10.10.2 using bootcamp.


@m15:

In my case when I used BC to set up a dual-boot system on my '10 MBPro, then when I wanted to add another partition, in my case for another version of OSX with linux . . . I couldn't.  Boot Camp had "frozen" the HD and no modifications could be done.  I had to wipe the whole drive and start fresh using Disk Utility to set up 3 partitions.  So, see if you can add a third partition/disk to make space for linux . . . if you can't modify the disk from OSX it's possible that until you wipe the drive you will have only two . . . so, you could possibly wipe the Windows data and install linux there . . . .

I have been wrong in my life and in linux many times, you have to find out what is real for you and your computer.  Try stuff . . . if your OSX system is backed up worst that can happen is . . . re-install.  OSX goes in first . . . then add other ingredients, flavor as needed, etc.

e...

---

### Post by mohamed15 on 2015-04-04
thanks este.el.paz for your comment. The point is as you mentioned, desk utility in OS X does not allow me to partition the hard disk into three partitions. I think the problem is in the word fusion drive. I read online that I need first to separate the ssd-type hard disk from the normal one and then go for partitioning and using refind. No way for me, as I am also new to such issues. What I found is someone installed ubuntu on external hard disk. Also, I read that any kind to partition fusion drive might cause irreversible damage to the hard disk and the whole system. Thanks anyway.
Mohamed

---

### Post by este.el.paz on 2015-04-04
> **mohamed15 said:**
> thanks este.el.paz for your comment. The point is as you mentioned, desk utility in OS X does not allow me to partition the hard disk into three partitions. I think the problem is in the word fusion drive. I read online that I need first to separate the ssd-type hard disk from the normal one and then go for partitioning and using refind. No way for me, as I am also new to such issues. What I found is someone installed ubuntu on external hard disk. Also, I read that any kind to partition fusion drive might cause irreversible damage to the hard disk and the whole system. Thanks anyway.
Mohamed

@M15:

Well, the question is whether DU **could*** have partitioned the drive **before** using Boot Camp . . . now, my experience showed me it would not because BC "locks" the hard drive . . . in some way.  But, right, if you did manage to break out of this situation rEFInd is what I am using, installed in the OSX system as the "boot selector" . . . not everyone seems to use it or GRUB, but my computer seems to "need" it.

So, no worries, linux will be around if and when you get there . . . or, as mentioned, you could erase the windows data and add the linux there.  Or, next probable best option . . . use Parallels or VMFusionware and install linux there; then the machine is running OSX, so no worries about fan control/heat issues . . . the linux OS is stored in the OSX partition . . . wherever it wants it . . . and no need to wipe the HDs and do a reinstall . . . "easy-peasy."

e..

---

### Post by mohamed15 on 2015-04-04
Again many thanks este.el.paz for these nice suggestions. I tried Parallel Desktop and yes it works, but I guess it will be more nicer, for me, to have ubuntu on a separate partition. Anyway, I wish the people for the coming new ubuntu (v15 or so) could take into account this point (fusion drive) and allow more flexibility with ubuntu installation (and thus ubuntu will be more popular). I will try your idea of either install ubuntu on windows partition or erase windows and see if disk utility is now able to partition the hard disk to three partitions. Many thanks again.
Mohamed

---

### Post by este.el.paz on 2015-04-04
> **mohamed15 said:**
> Again many thanks este.el.paz for these nice suggestions. I tried Parallel Desktop and yes it works, but I guess it will be more nicer, for me, to have ubuntu on a separate partition. Anyway, I wish the people for the coming new ubuntu (v15 or so) could take into account this point (fusion drive) and allow more flexibility with ubuntu installation (and thus ubuntu will be more popular). I will try your idea of either install ubuntu on windows partition or erase windows and see if disk utility is now able to partition the hard disk to three partitions. Many thanks again.
Mohamed

@M15:

Entirely up to you, but, really for right now, given that ***probably*** BC has "locked" your drive, Parallels might be your best choice.  A few years ago, when processors were "slow" there might have been some noticeable lag in speed if using a virtual OS . . . it would probably be negligible these days.  And, since you are "in OSX" any files you have there can be accessed w/o re-booting, etc.  It's the "best of all worlds" IMHO.  I haven't gone that way with my '10 MBPro because, well, I got started with PPC dual-boot . . . and, well, money is tight . . . so I try the free things first.  Given that linux is changing its OS every 6 months or so, the hassle to get one of them installed doesn't exactly calc out in cost/benefit time spent for giggles received . . . with Parallels you can just keep adding new OSs . . . .

Back to your install process, so wiping Windows is only going to open up that space that you could then install linux into . . . it won't **probably*** let you add another partition into the mix--as BC is likely going to maintain its iron grip on the HD.  Only way around that is wipe the whole drive (what I did) . . . clone OSX first to an Ext HD . . . wipe internal drive(s) . . . repartition them to roughly 3 disks . . . add OSX back +rEFInd . . . windows ??? . . . and then linux into the third.  If you have the third set up as "free space" or perhaps FAT32 then **maybe** the linux installer will recognize that space and set it up using "automatic" . . . .  Or, other option, select "manual" and then when GParted window opens search for the fusion drive and see if it shows up there; it may be able to do the install if you can select it in GParted.  Personally I haven't been able to get an install into an ext HD without it leaving data in the drive I was booted in . . . hence my suggestion to use Parallels.

As far as "15" recognizing fusion drive . . . maybe, but 15 is already in testing, they've made some internal changes so it's seemingly still very "cid-like" i.e., rough edges, and really linux is set up for PC . . . which obviously has multiple drive potential . . . but I don't know where "fusion" drive falls in that spectrum . . . if it's just SSD . . . then perhaps it could work . . . .  Try booting the install disk and see if you can see the various drives listed in GParted, if it's "stacked" in the main drive list you should be able to install to it . . . especially with "manual" . . . .  You can always cancel out of the install.  Enjoy the process . . . again, Parallels probably direction of least resistance . . . no worries about fan control issues . . . .

e..

---

