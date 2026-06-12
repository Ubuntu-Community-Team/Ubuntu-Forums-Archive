---
title: "Mac Mini - memory shortage &amp; disk thrashing"
date: 2009-04-25
forum: Apple Hardware Users
---

### Post by benmoreassynt on 2009-04-25
I have two almost identical computers, in terms of basic specs:
1.Old Compaq Laptop with 1GB RAM and 1 modest Pentium 4 2GHz CPU
2. Mac Mini with 1GB RAM, 1 Intel Core Duo CPU.

In theory the Mac's specs are better, but it is struggling to run Ubuntu Intrepid (64bit version) without disk I/O thrashing. Basically running more than a couple of applications causes it to hang for minutes at a time. Running Firefox and Thunderbird at the same time is too much, and I've turned off most possible memory intensive things like Compiz.

Using system monitor, I see that RAM usage hovers between 80 and 90% most of the time, and virtual memory usage will be about 500MB out of 3GB.

Any ideas as to a solution? While I can see that RAM is at the root of the issue, which of course can't be upgraded on a Mini, I don't understand why it is having so much more problems than the Compaq. 1GB of RAM is lowish these days, but not exactly tiny, and the CPU is ok.

---

### Post by cyberdork33 on 2009-04-25
what is the hard drive speed? That may be a key difference when having to cache to disk often (swap).

---

### Post by benmoreassynt on 2009-04-25
Its a 5400 RPM SATA, so pretty standard. The thing is, I don't think it should have to cache so often. The Compaq laptop has similar specs, and basically never uses the cache.

Is runnig 64bit Ubuntu likely to make greater demands than 32bit? I assumed that with 64 bit capability it made sense to use it.

---

