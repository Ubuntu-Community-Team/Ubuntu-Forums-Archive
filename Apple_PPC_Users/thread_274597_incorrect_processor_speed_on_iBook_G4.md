---
title: "incorrect processor speed on iBook G4"
date: 2006-10-10
forum: Apple PPC Users
---

### Post by sarsboy888 on 2006-10-10
Hi,

Been using Kubuntu 6.06.1 for a while now and I was rummaging through the different system apps and I noticed that my processor was running at half the speed it should.  I have an iBook G4 1.07 gHz but my /proc/cpuinfo shows the following:

```
+processor	: 0
+cpu		: 7447A, altivec supported
+clock		: 533.333000MHz
+revision	: 0.1 (pvr 8003 0101)
+bogomips	: 36.73
+timebase	: 18432000
+machine		: PowerBook6,5
+motherboard	: PowerBook6,5 MacRISC3 Power Macintosh 
+detected as	: 287 (iBook G4)
+pmac flags	: 0000001b
+L2 cache	: 512K unified
+pmac-generation	: NewWorld
```

Anyone know how to get the clock speed up to 1.07 gHz?

Edit:  I'm an idiot, it's just the processor scaling.

---

