---
title: "Is there any way to clear the Swap area?"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by RKCole on 2007-05-02
Hello, veryone.

Before I begin this post, here are the specs for my system:

Dell Dimension 4600i
Primary HDD: 250GB (with only Windows isntalled.  This one's not too important)
secondary HDD:  Ubuntu 7.04 (GNOME)
     hdb1: Root partition (5GB)
     hdb2:  Home partition (65GB)
     hdb3:  FAT32 Backup partition (8GB)
     hdb4:  Swap area (1.5GB)
256MB PC2700 DDR/SDRAM
Generic nVidia GeForce FX 5500 AGP card with 256MB onboard RAM

I know that some of this probably is not relevant.

I do not have much of a problem when I use my system, but everyone else in the household complain that the system begins to lag after awhile.  They all play Flash/Java games via Firefox, so I think taht this may be the issue--Firefox using up what little memory I have.

The issue is that my swap area reaches around 217MB usage, and things begin to run slowly after time.  As I've mentioned in previous threads, I cannot afford RAM quite yet, but i wish to eventually invest in at least 1GB.

Is there some way to clear swap and restore speed to the system without having to reboot?  I have tried:
```

sudo swapoff -a && sudo swapon -a

```
however I do not think that this command will work as the swap is already being used.  Is there anythign I can do?

Would the use of Swiftfox make any difference?

Thanks for any help and/or suggestions.

Take care.

---

### Post by Sef on 2007-05-02
> Would the use of Swiftfox make any difference?

[Swiftfox]("http://en.wikipedia.org/wiki/Swiftfox") has been discontinued.

> 256MB PC2700 DDR/SDRAM

Once you buy more ram, the problem will clear up as you have stated.

I know of no way to clear swap that is in operation.

---

### Post by mcduck on 2007-05-02
Like Sef said, the problem is not swap, it's that you have only 256MB of memory and your computer actually has to use swap (which is roughly 1000 times slower than using RAM).

You should try to at least double that RAM into 512MB, although if you are running Gnome 1GB would be nice.

---

### Post by mahiyar on 2007-05-02
Read this to get a good understanding of swap space and how to control  [http://www.xenotime.net/linux/doc/swap-mini-howto.txt](http://www.xenotime.net/linux/doc/swap-mini-howto.txt) .

---

### Post by RKCole on 2007-05-03
Thanks, Sef, mcduck, and mahiyar.

My birthday's coming up in July, so maybe I'll get lucky and get that 1GB of RAM I've been asking for. :)  Hope my wife's feeling generous.

That article was quite insightful.  **swapd** sounds interesting.  Think it's still in development?

Thanks again, and take care.

---

