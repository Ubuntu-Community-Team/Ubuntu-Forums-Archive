---
title: "Using already the double processor?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2007-04-24
HI everybody
I have had a doubt snce three weeks and nobody has answered me :???: but anyway, I have a new one (hope you answer it) Is ubuntu supporting the turion64 x2 already? or does it still has the problem of using only one and overheating ? (It would be niche  if someone knows about a HP Compaq nx6325 specially).

---

### Post by Happy_Man on 2007-04-24
If you use 64 bit ubuntu, then you get two cores. I'm not sure how 32 bit Ubuntu works on 64 bit systems, though.

---

### Post by bobplano on 2007-04-24
i think what he is saying is if you use the 64-bit version, for some reason it only uses one core and overheats. i'm pretty sure the 32-bit version runs on only one core anyway

---

### Post by Jorge32 on 2007-04-24
yes that's what I mean, does ubuntu supports the use of double core? or do I have to keep on waiting till it comes a version that supports my double 64 bit core?

---

### Post by marko_4454 on 2007-04-24
I have Intel Pentium D Dual core and it works in the i386 32 bit ubuntu.
You can check in the system monitor if its supported. 
I dont know if there are any issues for turion...but there should be support

---

### Post by Jorge32 on 2007-04-25
ok ok anyway, if anyone has an ubuntu laptop with turion64 x2 Ill appreciate any help, thanks

---

### Post by igknighted on 2007-04-25
> **Jorge32 said:**
> ok ok anyway, if anyone has an ubuntu laptop with turion64 x2 Ill appreciate any help, thanks

It is running 2 cores.  The generic kernel has SMP (symmetric multi processing) support built in.  If you are using a different kernel for some reason it might not, but the default kernel supports it.

---

