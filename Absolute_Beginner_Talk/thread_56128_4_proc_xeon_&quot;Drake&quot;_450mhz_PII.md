---
title: "4 proc xeon &quot;Drake&quot; 450mhz PII"
date: 2005-08-11
forum: Absolute Beginner Talk
---

### Post by rherman on 2005-08-11
I have the opportunity to get a free quad system with raid. I realize it's outdated hardware, but it has 4 processors with 1mb cache each. Would Ubuntu run on this? I am thinking on using it as a supplement to my main pc for rendering or other such things. Thanks.


Rob

---

### Post by jasmuz on 2005-08-11
Surely it must run, but RAID has given many people problems on install, please consult the forums on a search.

---

### Post by KingBahamut on 2005-08-11
Ive got Ubuntu Running on a proliant 1600 Dual 300s and a 4 14.3gig scsi drives. I set the raid up post install however, so I cannot speak on RAID at install. 

If Ubuntu will run on my Proliant, it will surely run on your xeon box. No question.

---

### Post by rherman on 2005-08-11
I'm running ubuntu on my dual 1.2ghz athlon mp with a hardware raid 0. Ubuntu did nothing, the Raid is there from the get go. I was more interested in knowing if 4 450mhz xeon processors will run better than my more modern, 1999 vs 2001 setup?

It does run.

Rob

---

### Post by varunus on 2005-08-11
Ubuntu/Linux in general can handle 4 xeons.  Though you'll need to install the "smp" (symmetric multi-processor, if my acronym memory serves me correctly) kernel from synaptic for them to all be used.

Now, which one will be faster...that's a different story. It really depends on what you're doing.  Many applications don't use more than one process, one thread, so the 450 will be slower than on the 1.2.  Apps that can take advantage of the 4 processors, they might be faster than on the 1.2.  Its really a per-application thing.  Though, two 1.2 Ghz vs. 4 450...I think the newer, more modern architechture will go faster in general.

You may want to look into OpenMosix in a few months, which lets regular processes and not just multithreaded apps spread between processors.  Openmosix is designed for clustering over a network, but if you install it on a multiprocessor PC it will pretend you have a 4 processor cluster computer, further increasing your performance.  Unfortunately, it just got ported to kernel 2.6, and the userspace process handler isn't done yet, so you may want to look into it later...

---

### Post by poofyhairguy on 2005-08-12
[QUOTE=rherman]I have the opportunity to get a free quad system with raid. I realize it's outdated hardware, but it has 4 processors with 1mb cache each. Would Ubuntu run on this? I am thinking on using it as a supplement to my main pc for rendering or other such things. Thanks.


Rob[/QUOTE]

How much RAM it has matters more. With 256mb+ that thing would run nicely.

---

### Post by rherman on 2005-08-18
2 gigs of ram. OpenMosix sounds like a nice way to add the additional processing power of the older machine. Hey, it's free. Then I will not have to upgrade my current computer for another 2 years! Thanks.

rob

---

