---
title: "[SOLVED] How much physical RAM is my system using?"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by keymoo on 2007-09-09
Hi,

I have Ubuntu Server running but two different programs are reporting differing amounts of RAM being used by the system - how do I know which one to believe?

**saidar reports**
mem total: 1011M Mem Used: 993M

**webmin reports**
Real memory: 1011.47 MB total, 138.18 MB used

Which one do I believe?

Thanks.

---

### Post by DBStevens on 2007-09-09
Both are likely correct.

You are using two different systems running at two different times.

Both are reporting essentially the same real memory.

I don't know how either of them decides what consitutes used memory, nor do I know the relative difference between the memory requirements of the two tools when they run.

---

### Post by insane_alien on 2007-09-09
this is to do with the way linux manages memory. the total amount of RAM that actually contains data is 993MB

if you take away the cache and buffers so it's only what applications and the OS is using then it is 138.18 MB

if you do ```
free -m
``` it will lay it out in a more telling way.

---

### Post by sumguy231 on 2007-09-09
Sounds like one might be counting cached memory as used (saidar) while the other reports it as free (webmin). You can do a 'free -m' for a more detailed report.

---

### Post by keymoo on 2007-09-09
Thanks

free -m:
```
             total       used       free     shared    buffers     cached
Mem:          1011        995         16          0         17        852
-/+ buffers/cache:        125        885
Swap:         1906          0       1905
```

---

### Post by jordanmthomas on 2007-09-09
This means that you have 125 MB of "physical RAM" actually being used.  Once you add in stuff that has been used recently but is not still being used (buffers / cache), you are using 995 MB, which is fine.  

Using up all your RAM in Linux is not a bad thing.  It's designed to take advangtage of everything it can.  After all, unused RAM is useless RAM, right?
```
             total       used       free     shared    buffers     cached
Mem:           495        483         12          0         52        128
-/+ buffers/cache:        302        193
Swap:          784          0        784

```
Now, I am actually using 302 MB of RAM with another 181 reserved, but still available and another 12 that are completely unused.

I hope that makes some sense

---

### Post by keymoo on 2007-09-09
Thanks to everyone that replied to this thread. I understand it now.

---

