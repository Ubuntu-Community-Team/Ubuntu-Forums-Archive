---
title: "Multi-core Processor Support in Feisty"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by bagrol1 on 2007-04-20
Does Feisty support dual or quad core processors???  I've read some buzz phrases such as "SMP supported by generic kernel" or "rebuild the kernel" which I have no clue what they mean.

Do people  with these multi core processors have them fully recognized with standard Feisty installations or only ONE core is recognized and for full support (SMP????) some steps need to be taken? I plan to build a new comp for Linux with dual or quad processor and would like the investment to pay off.

Thanx.

---

### Post by lamalex on 2007-04-20
typeh
```
uname -a
```
in the terminal, if you see SMP you're good. It should be already there, if it's not then somehow your installation was different from everyone elses. You should be good to go.

---

### Post by Cicatrix on 2007-04-20
[http://en.wikipedia.org/wiki/Linux_kernel#Architecture](http://en.wikipedia.org/wiki/Linux_kernel#Architecture)

The linux kernel has supported multi core for a long time, since 1996, so I guess you will be able to get some use from more than one. :)

---

### Post by thesphine on 2007-04-20
The Generic kernel that feisty uses out of the box has no problem with my Dual Athlon MP's - So no need to use the old SMP kernel packages or build your own.

---

### Post by kpel on 2007-04-20
I installed Feisty on a Core 2 Duo (Conroe E6600) machine and have had dual-core support from the start.  The frequency scaling monitors even report individual core frequency scaling, though I don't know if that is accurate or not.

---

