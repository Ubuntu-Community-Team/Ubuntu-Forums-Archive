---
title: "partitioning and booting woes"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by nbv4 on 2007-10-19
Every single time I try to install linux, I end up with this same problem.

[[img]http://xs220.xs.to/xs220/07425/Screenshot-Install.png[/img]](http://xs.to)

I have a 200 Gig IDE drive thats FAT32 and I want it mounted at /storage
I have a 400 Gig SATA drive thats ext3 and I want it mounted at /home

I have a 80 gig SATA drive that is in 4 equal partitions of 20 gigs each
One 20 gig partition has windows XP
the second one is unpartitioned and empty
the third one is where I plan to have ubuntu
and the fourth one is for swap

This I think I have all sorted out, but where do I put /boot?

After I installed linux exactly as shown above, after a restart, only WinXP came up. I tried messing around with my boot order in the BIOS settings, but all I could come up with was a Grub error #22 (whatever that means)

---

### Post by p_quarles on 2007-10-19
You don't need to make a separate boot partition. The problem is that you have the root filesystem set up as a logical partition, which isn't bootable. Get rid of sdb6 and create a new primary partition for the root filesystem ( "/" ). That should take care of it.

---

### Post by nbv4 on 2007-10-19
> **p_quarles said:**
> You don't need to make a separate boot partition. The problem is that you have the root filesystem set up as a logical partition, which isn't bootable. Get rid of sdb6 and create a new primary partition for the root filesystem ( "/" ). That should take care of it.

how can you tell (how can *I* tell) that it's a "logical" partition and not a "primary" partition?

---

### Post by p_quarles on 2007-10-19
> **nbv4 said:**
> how can you tell (how can *I* tell) that it's a "logical" partition and not a "primary" partition?
I can tell because you can only have four primary partitions to a drive . . . and Linux numbers them 1 through 4. 

When you're making a new partition, the program gives you the option of checking "logical" or "primary"  . . . just choose primary, and it will be created as sdb2.

---

### Post by LowSky on 2007-10-19
you dont need 20GB for swap, that is way overkill. the most you need is 2GB

what with the numbering 1,5,6,7, that makes no sence and doesn't work. should be 1,2,3,4

---

### Post by nbv4 on 2007-10-19
> **p_quarles said:**
> I can tell because you can only have four primary partitions to a drive . . . and Linux numbers them 1 through 4. 

When you're making a new partition, the program gives you the option of checking "logical" or "primary"  . . . just choose primary, and it will be created as sdb2.

oh, I see. I was wondering why there was a gap in the numbers. One more question, can the swap partition be logical? Thanks for your help!

---

### Post by mikeyphi on 2007-10-19
> **nbv4 said:**
> how can you tell (how can *I* tell) that it's a "logical" partition and not a "primary" partition?

You will have to redo the partition and select the 'new' partition as Primary instead of Logical. If you use gparted to do your partitioning it's a fairly obvious choice on the GUI.

---

### Post by p_quarles on 2007-10-19
> **LowSky said:**
> you dont need 20GB for swap, that is way overkill. the most you need is 2GB
The swap partition is 1.7. gigs. Look again.
EDIT: Looked again my own d*** self and noticed the zero. My bad. 

> **nbv4 said:**
> oh, I see. I was wondering why there was a gap in the numbers. One more question, can the swap partition be logical? Thanks for your help!
Yeah, the swap partition can (and should) be logical. The program will set that up automatically for you anyway.

---

### Post by nbv4 on 2007-10-19
> **LowSky said:**
> you dont need 20GB for swap, that is way overkill. the most you need is 2GB

After nixing ubuntu a few days ago after a botched gutsy upgrade, I noticed my / partition had only like 6 gigs of data on it. I though, whats the point of having the whole thing on a 80GB partition when you're only going to use less than 10% of it? I thought maybe it would get more use as swap...

---

### Post by Sef on 2007-10-19
> After nixing ubuntu a few days ago after a botched gutsy upgrade, I noticed my / partition had only like 6 gigs of data on it. I though, whats the point of having the whole thing on a 80GB partition when you're only going to use less than 10% of it? I thought maybe it would get more use as swap...

Most people don't need more than a GB of swap at the most.  If you have more than a GB of ram, most likely you don't need swap at all, unless you are doing movie editing or some other ram intensive process.

---

### Post by nbv4 on 2007-10-19
When it asks me what device to install the boot loader onto, which do I put? The device that I have my partitions installed onto? The default is (hd0), which is my storage drive. Will this option even matter?

---

### Post by p_quarles on 2007-10-19
Use the default. The only way it would matter is if you frequently swap out hard drives, which most users don't.

---

