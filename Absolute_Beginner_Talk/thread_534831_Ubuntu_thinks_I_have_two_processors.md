---
title: "Ubuntu thinks I have two processors?"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-08-25
I opened up the System Monitor, and under the System tab, it says that I have two processors: Processor 0: Intel Pentium 4 CPU 3.00 GHz, and Processor 1: Intel Pentium 4 CPU 3.00 GHz.  Furthermore, it under the Resources tab, it gives me the CPU usage for both processors.  I am almost 100% sure that the Pentium 4 processor has only one CPU, so I am wondering why Ubuntu thinks that I have two.

Thanks.

---

### Post by Steveway on 2007-08-25
That seems to be one of those Hyperthreading Cpus.
I can't tell for sure, cause I only have AMD-Cpus.

---

### Post by Majorix on 2007-08-25
I can remember someone else reporting the same problem a few months ago. So probably since you both can compute it is not that a bad thing.

---

### Post by Yes on 2007-08-25
Yeah, everything seems to be working fine, I just wanted to know if anything more was known about why this could be happening.

Thanks.

---

### Post by mcduck on 2007-08-26
That's a P4 with Hyper-threading. This means that the CPU reports itself as having 2 cores (while there really is only one). This way it can share the CPU time a bit more effectively between multiple running programs, when a program running in the 1:st virtual CPU stops to wait for some data the CPU starts running program from the 2:nd virtual CPU.

[http://en.wikipedia.org/wiki/Hyper-threading]("http://en.wikipedia.org/wiki/Hyper-threading")

---

### Post by Paulmd on 2007-08-26
> **Yes said:**
> Yeah, everything seems to be working fine, I just wanted to know if anything more was known about why this could be happening.

Thanks.

Just hyperthreading.
[http://en.wikipedia.org/wiki/Hyper-threading](http://en.wikipedia.org/wiki/Hyper-threading)

---

