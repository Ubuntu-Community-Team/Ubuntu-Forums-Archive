---
title: "Recomended Swap Partition size?"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by GingerAlex on 2007-05-17
Hello,

when setting up my system I read somewhere that swap space should be twice physical memory, as a rule of thumb.

I have 1Gb memory, so I went for 2.3Gb swap. Thought I wouldn't want to run out!

Thus far I have never seen more than 32Mb of swap space employed. So have I wasted a lot of disk space? If so what is a sensible rule for swap space?

regards,
Alex

---

### Post by Bachstelze on 2007-05-17
Having that much swap will be needed only if you want to use suspend-to-disk. Otherwise, you can resize it down to 512 MiB.

---

### Post by Cypher on 2007-05-17
I always use the rule swap space = total memory. So you could've used 1GB. But at the same time, you could have easily gotten away with 512MB for swap space.

Without enough available RAM space, Linux wouldn't need to go to swap unless you have a large number of applications taking up a lot of memory. So in general use, you'll seldom see any SWAP usage at all..

So the ultimate answer, I guess, lies in how you will be using the machine as opposed to a hard and fast rule of RAM multipliers..

---

### Post by lintoolman on 2007-05-17
In the past , I've used anywhere from 1/1 ram/swap to 1/1.5 ram/swap.  Now that I use machines with 4g ram the few times I've check, no swap was being used.

There are ***_rare _***cases where amount of total memory (ram+swap) will be critical.  For example, re-mastering knoppix.  The last time I remastered a knoppix DVD, 5g of total memory was required.  This still did not necessitate the need for large swap partition, as I added swap space to bring up my total memory to the required amount.

On my long list of things to research is how running multiple VMware images affects my swap usage. Maybe that will change my opinion.

---

### Post by GingerAlex on 2007-05-18
thanks for the advice, appreciated.

cheers,
Alex

---

