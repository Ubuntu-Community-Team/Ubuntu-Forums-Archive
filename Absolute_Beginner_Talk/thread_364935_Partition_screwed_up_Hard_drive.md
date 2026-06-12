---
title: "Partition screwed up Hard drive"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by Drake250 on 2007-02-18
So I got a free computer that I decided would be a perfect time to try out that Ubuntu system I've been hearing so many great things about.

I used the Live CD and got to the partitioning part of the installation. Now I have very little knowledge on what partitions are so I went with default options.

Ubuntu froze, and it didn't change after over 3 hours of letting it do whatever it was trying to do. I turned off the computer and re-booted it, re-ran the installer, and now when I get to step 5 it hangs while looking for hard drives. Ubuntu is still responsive. I can do anything but proceed with installation.

The Disks Manager sees two hard drives now. Both of their Types are Unknown, and Both of their Speeds are Unavailable. The first hard drive Device is "tmpds", the second is "unionfs". Nothing else even knows a hard drive is there (I tried to use both the GParted in Ubuntu, and the Live CD version of GParted alone).

I put the hard drive as a slave drive in my Windows machine (like I did to format it before I planned to install Ubuntu), but now it does not come up at all.

So if anyone knows how to revive this hard drive I would be very grateful. There's nothing on it so any form of re-formatting is fine with me.

Thanks

---

### Post by Patrick K on 2007-02-18
You might want to download the mfg's diagnostic utility and run it. More than likely it will fix the problem.

---

### Post by irish_flu on 2007-02-18
Just to make sure I understand: the Ubuntu installer can't see it, and Windows also can't see it?

When you were installing Ubuntu, did you let it "erase entire disk"?  That might help; if the problem is partition-related.

On the other hand, it could be a hardware issue.  Does the disk make any "funny" noises?

Get into your BIOS (as the computer starts up, often called "setup") and see if the drive is recognized in there.

If the disk is really and truly failing, there's no "reviving" it that will last more than a few hours or days.  However, if it's just a partition problem then erasing the current partition (as I mentioned earlier) ought to make it work just fine for you.

---

### Post by Drake250 on 2007-02-19
Forgive me for my stupidity but what is the mfg's diagnostic utility? I'm assuming you mean Manufacturers. In that case Western Digital's Lifesaver thing could see two hard drives but do nothing about it (arg). If anyone could provide a link to the program/cd/etc I need to download please do. I've never done any of this stuff so it's all new to me.

My BIOS says there is no Hard Drive also, I'm thinking I may have killed this drive. Pitty it was an 80GB free hard drive.

Well if anyone else has any ideas for this drive please post. Thanks for the mfg's diagnostic utility, this forum is very nice and friendly. It's nice to know that my new OS will have a great place to look for support

BTW, I got Ubuntu working on an extra 40GB Hard drive I wasn't using. Ubuntu is great and very fast.

---

### Post by ieee488 on 2007-02-19
I had a WD drive that went bad on me.

There should be a feature in the Data Lifeguard Tools to do a scan of your hard drive.

Running that function told me that the drive was going bad fast.

---

### Post by rusty4r on 2007-02-19
I think that the drive was already going down and one more format did the trick.

---

### Post by irish_flu on 2007-02-20
> **Drake250 said:**
> 

My BIOS says there is no Hard Drive also, I'm thinking I may have killed this drive. Pitty it was an 80GB free hard drive.

One thing's for sure, you probably didn't kill it.  If it died, it's probably because of either mechanical failure, or failure of the controller (nothing you did).  :)

---

