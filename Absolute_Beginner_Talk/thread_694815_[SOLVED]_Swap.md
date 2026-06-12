---
title: "[SOLVED] Swap"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by dwally89 on 2008-02-12
Hi,

I'm still quite new to Ubuntu, and am not sure if I have a swap partition.

When I go onto the System Monitor, on the Resources tab, under the Used Swap it says 0 bytes of 0 bytes. I assume this means I have no swap?

I have 2GB of RAM, so do I need Swap?

Thanks

---

### Post by oilchangeguy on 2008-02-12
> **dwally89 said:**
> Hi,

I'm still quite new to Ubuntu, and am not sure if I have a swap partition.

When I go onto the System Monitor, on the Resources tab, under the Used Swap it says 0 bytes of 0 bytes. I assume this means I have no swap?

I have 2GB of RAM, so do I need Swap?

Thanks

no

---

### Post by emarkd on 2008-02-12
You have no swap. If you created a swap partition it's not getting mounted.  Unless you're running out of RAM, you don't really need one.  They're nice to have, though, if you do lots of things at once or get involved with lots of multimedia stuff.

---

### Post by dwally89 on 2008-02-12
Thanks

---

### Post by neurostu on 2008-02-12
When you installed ubuntu, did you let ubuntu handle the partitioning of the hard drive or did you partition it yourself?  If you did it yourself then you need to manually create a swap partition.  

You said that you have 2 gb of ram which is more then enough, but swap is nice b/c the system can use it to put away large amounts of memory that aren't being used but will be accessed in the future.   You do not need a swap as you have a lot of ram but it will help and your system will perform better with swap. 

Unless your HDD is small and you are cramped for space I would highly recommend having a swap partition.  Unfortuneatly the only way I know how to configure the swap partition is to do it during install. 

So if your ubuntu installation is newer and you can afford to reinstall I would:

1- Create a swap partion using GParted (about 3-4 gb in size)
2- Reinstall Ubuntu - select the new partition under the partition manager to be your swap partition


Good luck!

---

### Post by FuturePilot on 2008-02-12
With that amount of RAM you probably won't need it. But it's probably a good thing to have. You won't be able to hibernate you computer with out it, and if you do a lot of heavy multi-tasking or multimedia stuff you're probably going to want some swap.

---

### Post by emarkd on 2008-02-12
If you do decide you want a swap partition, you don't have to reinstall to get one.  You can just gparted to break off some (at least 2 Gig if you want to be able to hibernate) and format it as swap, then add it to your fstab and remount everything.  It won't be hard.

---

### Post by oilchangeguy on 2008-02-12
> **neurostu said:**
> When you installed ubuntu, did you let ubuntu handle the partitioning of the hard drive or did you partition it yourself?  If you did it yourself then you need to manually create a swap partition.  

You said that you have 2 gb of ram which is more then enough, but swap is nice b/c the system can use it to put away large amounts of memory that aren't being used but will be accessed in the future.   You do not need a swap as you have a lot of ram but it will help and your system will perform better with swap. 

Unless your HDD is small and you are cramped for space I would highly recommend having a swap partition.  Unfortuneatly the only way I know how to configure the swap partition is to do it during install. 

So if your ubuntu installation is newer and you can afford to reinstall I would:

1- Create a swap partion using GParted (about 3-4 gb in size)
2- Reinstall Ubuntu - select the new partition under the partition manager to be your swap partition


Good luck!

please explain how the system can "put away large amounts of memory" to be used in the future? and why would you need 3-4 gb of swap? check to see just how much swap your computer is NOT using, before making these kinds of statements.

---

### Post by neurostu on 2008-02-12
when I was installing ubuntu, I was advised that you should create a swap partition of about twice the size of your ram.

---

### Post by max renn on 2008-02-12
My system used over 3.5GB ram/swap when I ran Adept manager and downloaded all 129 updates at once.

---

### Post by emarkd on 2008-02-12
> **max renn said:**
> My system used over 3.5GB ram/swap when I ran Adept manager and downloaded all 129 updates at once.

Wow.  My desktop has 2 Gig and 1 Gig swap and I've never seen it even come close to using it all  --  and I ask a lot from my computers.

---

### Post by max renn on 2008-02-12
> **emarkd said:**
> Wow.  My desktop has 2 Gig and 1 Gig swap and I've never seen it even come close to using it all  --  and I ask a lot from my computers.

LOL, yeah, I was watching it climb ,little by little, worried it would hit four gigs and fail.  Funny thing is, I always ran windows without a swap and never went over 1.25GB usage.  Then, I switch to linux and peg 3.5GB.  Something wrong with that picture?!?

---

