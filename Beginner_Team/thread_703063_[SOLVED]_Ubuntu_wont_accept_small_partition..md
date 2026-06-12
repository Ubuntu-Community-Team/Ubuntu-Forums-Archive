---
title: "[SOLVED] Ubuntu wont accept small partition."
date: 2008-02-20
forum: Beginner Team
---

### Post by BurKaBU on 2008-02-20
I've finally worked up the courage to install Ubuntu on my laptop HP nx9420 and are actually very excited about a new challange.
The problem is since I only have a laptop with limited disk space (100gb) and I'm not ready to give up on windows until I gain some more knowledge and confidence in Ubuntu I wanted to start out small with only 10gb reserved for Ubuntu. (and from what I understand it shouldn't be a problem to start at 10gb and then mount the rest of HD further down the line)

But the problem is that the installation wont let me make a partition that small, the automatic want me to use at least 75gb and the manual one wont let me put in 10gb :'(

Would really appreciate if someone could help me out with this.

ps. I've been browsing around trying to find out if you can get a Razer diamondback working well in Ubuntu, and by well i mean assign ctrl and shift to the buttons on the side... this is actually one of the biggest concerns i have about Ubuntu. 
I don't have any programs in particular that I can't do without, but my precious mouse is a "must have" :)
So if anyone could give me a "yes", "no" or "maby" in the matter it would be greatly appreciated :)

-Peter

---

### Post by MobiusNZ on 2008-02-21
10gb should be fine. I'm currently using 4GB of my available 200GB (that I have partitioned for linux).

Most likely the problem when you're manually partitioning is you don't have the right partitions. At minimum you need a / (root) partition, plus a swap partition. Try making a / partition of 10gb or so and a swap partition equal to the amount of RAM you have, but no less than 1gb.

---

### Post by LaRoza on 2008-02-21
> **MobiusNZ said:**
> 10gb should be fine. I'm currently using 4GB of my available 200GB (that I have partitioned for linux).

Most likely the problem when you're manually partitioning is you don't have the right partitions. At minimum you need a / (root) partition, plus a swap partition. Try making a / partition of 10gb or so and a swap partition equal to the amount of RAM you have, but no less than 1gb.

512 MB of swap is fine. People have seen no difference between 256 MB of Swap and 512 MB, so more is way overkill.

---

### Post by MobiusNZ on 2008-02-21
> **LaRoza said:**
> 512 MB of swap is fine. People have seen no difference between 256 MB of Swap and 512 MB, so more is way overkill.

You're probably right. I find it hard to not overkill though, when I have more hdd space than I know what to do with ;).  'Sides, I figure it can't hurt having a 10gb swap file (I just looked at my partition table now).... can it???

---

### Post by MobiusNZ on 2008-02-21
> **BurKaBU said:**
> 

ps. I've been browsing around trying to find out if you can get a Razer diamondback working well in Ubuntu, and by well i mean assign ctrl and shift to the buttons on the side... this is actually one of the biggest concerns i have about Ubuntu. 
I don't have any programs in particular that I can't do without, but my precious mouse is a "must have" :)
So if anyone could give me a "yes", "no" or "maby" in the matter it would be greatly appreciated :)

-Peter

Anything is possible, its just a matter of how tricky it can be. In this case you're probably looking at manually editing config files - have a look at [http://ubuntuforums.org/showthread.php?t=28374](http://ubuntuforums.org/showthread.php?t=28374) for a starting point..

---

### Post by BurKaBU on 2008-02-23
tnx for the fast repplys, I'm used to post on forums one day and then log back in 2 days and hope for 1 repply =)

Anyways I still cant get ubuntu to accept a 10gb partition.
But at least i know know there are a possibility to use my precios mousebuttons =)

---

### Post by MobiusNZ on 2008-02-23
> **BurKaBU said:**
> tnx for the fast repplys, I'm used to post on forums one day and then log back in 2 days and hope for 1 repply =)

Yeah, the buntu forum rocks ;)
> **BurKaBU said:**
> 
Anyways I still cant get ubuntu to accept a 10gb partition.

Are you getting an error message? What does it say? When you create the partition, what mount point did you give it? Did you create a swap partition as well?

---

### Post by BurKaBU on 2008-02-24
.

---

