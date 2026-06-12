---
title: "A few questions before I install Ubuntu..."
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by roxybudgy on 2006-10-06
Previously I installed Ubuntu on my old laptop. Now I'm thinking of installing it on my new laptop (which I use for just about everything).

My new laptop has two partitions (c drive and d drive). C drive has Windows XP, programs, and my important files. D: contains large files that are waiting to be bunred onto a DVD.

I want to keep Windows XP just in case (after all, I'm still new to this Ubuntu stuff), so I'm thinking of installing Ubuntu on D: so before I get started, I have a few questions...

Will I need to clear all the files off D drive to install Ubuntu?

Can I still access the files on C drive when using Ubuntu installed on D drive?

Will I need to set up Internet connection for Ubuntu? It's all set up in Windows XP already, and it was a real problem trying to set it up on my old laptop.

What about programs that are already installed. Can they be used? for example, I prefer using Opera, will I need to install it again, having two copies of Opera installed on the laptop?

---

### Post by kidders on 2006-10-06
Hi there,

> **roxybudgy said:**
> Will I need to clear all the files off D drive to install Ubuntu?
You don't absolutely *have* to, but you really should ... you'd be installing Linux on an NFTS/FAT partition, which would be totally crazy.

> **roxybudgy said:**
> Can I still access the files on C drive when using Ubuntu installed on D drive?
Probably.

> **roxybudgy said:**
> Will I need to set up Internet connection for Ubuntu?
Only if you want Ubuntu to have internet access.

> **roxybudgy said:**
> What about programs that are already installed.
Naturally, Opera for Windows won't run on Linux. Some apps might let you share your preferences though.

---

### Post by halitech on 2006-10-06
> **roxybudgy said:**
> 

Will I need to clear all the files off D drive to install Ubuntu?

Can I still access the files on C drive when using Ubuntu installed on D drive?

Will I need to set up Internet connection for Ubuntu? It's all set up in Windows XP already, and it was a real problem trying to set it up on my old laptop.

What about programs that are already installed. Can they be used? for example, I prefer using Opera, will I need to install it again, having two copies of Opera installed on the laptop?

As far as your D drive, yes  you will need to remove anything you want to keep unless you resize it and create in effect an E drive.

You will be able to access the drive with at least read only if it is NTFS, it is FAT32, you can get read/write access.

Yes, you will need to set up your internet connection again in Ubuntu

Do you mean use your windows programs in Ubuntu? if that is what you mean, then no.

---

### Post by roxybudgy on 2006-10-06
Thankyou everyone for answering my questions. It looks like I should get started on moving those files off D (I'll probably dump some of it into C, and then burn or delete the rest).

---

### Post by szf on 2006-10-06
> **kidders said:**
> 
You don't absolutely *have* to, but you really should ... you'd be installing Linux on an NFTS/FAT partition, which would be totally crazy.

To add to that - you *may* be able to non-destructively resize the D: drive, but I wouldn't count on it. If you want to preserve a D: drive for Windows at all (i.e. re-apportioning 50% of the available disk space for Ubuntu), you'll be well served by a full backup to DVD first. Btw, Linuxes have to concept of [Drive Lettername]... you're likely to see something like hda1 [Windows], hda2 [Data].  

> **kidders said:**
> 
Probably.

Agreed.

> **kidders said:**
> 
Only if you want Ubuntu to have internet access.

Did the OT say here that the hardware target is an old(er) laptop? You may not have to do anything to setup networking if you're going to use an ethernet cable... wireless is another story.

> **kidders said:**
> 
Naturally, Opera for Windows won't run on Linux. Some apps might let you share your preferences though.

Good suggestion, kidders...

Also, if possible. backup the Windows MBR (Master Boot Record) before an Ubuntu installation.

---

