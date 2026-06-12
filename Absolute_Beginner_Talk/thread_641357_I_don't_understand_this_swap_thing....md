---
title: "I don't understand this swap thing..."
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by Pogeymanz on 2007-12-15
I have 512MB RAM and made a 720MB swap partition (That made my main partition a nice number). When does the swap get used?? I've been running the System Monitor and I have not seen the swap partition get used yet. My RAM is using 140MB right now and has been for a while. Is there a way to test and see if my swap is working okay?

I just don't know when the swap is supposed to be used, so I don't even know if it's broken or not.

---

### Post by mellowd on 2007-12-15
It will generally only use the swap when you have completely exhausted your normal ram

---

### Post by DezSP on 2007-12-15
Indeed, and since Ubuntu runs quite happily with as little as 256 MB for normal tasks (unlike SOME operating systems *cough*), you probably won't see your swap being used much. If you want to test it, you could always get your PC to calculate Mersenne primes or something, but I wouldn't bother, chances are your swapfile is absolutely fine.

---

### Post by SunnyRabbiera on 2007-12-15
the swap is mainly used for an extra boost, even on higher systems its a good idea to have it.
Swap just relieves the load, it helps great when you run low specs like me.

---

### Post by Pogeymanz on 2007-12-15
Okay. I dig. Does Windows have it's own swap file/partition?

---

### Post by Whiffle on 2007-12-15
It has a file, but usually not a partition.  It does things a little differently.

---

### Post by Taboo Mirage on 2007-12-15
Execute this:

```
cat /proc/meminfo | grep -i swap
```

If you see figures being returned here, then you can fairly safely assume all is working as intended.

---

### Post by SunnyRabbiera on 2007-12-15
> **EmosSuck777 said:**
> Okay. I dig. Does Windows have it's own swap file/partition?

eh not really, windows is all inclusive in its memory use thus why its ultra slow 99.9% of the time

---

### Post by funrider on 2007-12-15
> **SunnyRabbiera said:**
> eh not really, windows is all inclusive in its memory use thus why its ultra slow 99.9% of the time

windoze uses pagefiles for "swaping"

[http://en.wikipedia.org/wiki/Paging](http://en.wikipedia.org/wiki/Paging)

---

### Post by DezSP on 2007-12-15
Windows can be made to use Linux swap partitions too.

---

### Post by Pogeymanz on 2007-12-15
It's amazing how little I knew about computers! All my previous knowledge of computers was only knowledge of Windows!

---

