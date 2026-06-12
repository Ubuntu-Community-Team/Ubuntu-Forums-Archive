---
title: "Question about my swap partition:"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by b33rnutz on 2006-07-17
I recently installed Ubuntu (you might have seen my last thread a few days ago ;) ) and having done a bt of research, I saw a majority of people saying that my swap should be 2x the amount of RAM I have. Because of this, I set my swap at 2 GB (I have 1 GB RAM,) but this seems to be overkill. I never see more than 20% of my RAM used, and I have never seen any of my swap used (I obsessively check out my system monitor...I'm used to frequent memory leaks in XP heh.)

Would it be ok to lower m swap to 1 GB, possibly even lower?

---

### Post by T700 on 2006-07-17
The 2x rule is really more applicable with smaller amounts of RAM.  With 1GB on board, unless this is a server, a CAD workstation, or the like, I'd personally set it for 256M.  Some people will eliminate it completely, but I'm a belt and suspenders kind of guy!

Paul

---

### Post by ahaslam on 2006-07-17
> **b33rnutz said:**
> Would it be ok to lower m swap to 1 GB, possibly even lower?

Yes, I would.
I would only recommend 2 x RAM for 512MB or less, max of 1G swap.

Tony.

---

### Post by taurus on 2006-07-17
The 2x of your RAM was an old method!!!  That was long time ago...  Since you have 1GB of RAM, you can create a swap of 512MB of even 1GB if you wish and chances are your swap will not be used at all, depending on what you do with your system.

---

### Post by az on 2006-07-17
> **b33rnutz said:**
> I recently installed Ubuntu (you might have seen my last thread a few days ago ;) ) and having done a bt of research, I saw a majority of people saying that my swap should be 2x the amount of RAM I have.?

This is a classic questions that starts religious wars.

> **b33rnutz said:**
> 
 Because of this, I set my swap at 2 GB (I have 1 GB RAM,) but this seems to be overkill. I never see more than 20% of my RAM used, and I have never seen any of my swap used (I obsessively check out my system monitor...I'm used to frequent memory leaks in XP heh.)

Would it be ok to lower m swap to 1 GB, possibly even lower?

Sure you can.  The only thing that needs your swap to be a particular size is hibernation.  Since putting a computer into hibernation writes the contents of memory to the swap partition, it needs to be about 25 per cent larger than your RAM.

Your swap size depends on your needs.  Unless you have particular needs, just let the installer decide how big a swap to use and forget about it.

If you want to shrink your swap, you will have to boot a live cd, turn off the swap since the live cd will try to use it

sudo swapoff -a

then delete the swap partition.  Extend your ubuntu partition and then re-create the swap with the remaining free space.

That is assuming you put your swap just after your ubuntu partition that you want to make bigger.

---

### Post by b33rnutz on 2006-07-17
Haha thanks...yeah, I'm new to this.

---

### Post by crystal on 2006-07-17
> Sure you can. The only thing that needs your swap to be a particular size is hibernation. Since putting a computer into hibernation writes the contents of memory to the swap partition, it needs to be about 25 per cent larger than your RAM.
In my case I have 1 GB of RAM and 1 GB of swap on a desktop computer. Suppose that RAM is nearly totally utilised and I try to enter hibernation mode, what will happen?

---

