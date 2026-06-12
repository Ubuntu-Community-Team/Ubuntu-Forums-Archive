---
title: "When are we *really* out of RAM?"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by blinkum on 2008-02-25
Hi folks,

I have an Ubuntu box, and I run a certain software on it which consumes a lot of memory in time. My approach to memory management is very lazy, I want to reboot the box when I run out of memory.

I guess in Linux, there are a lot of ways to learn the memory usage, I can say top, vmstat, cat /proc/meminfo and etc.

Now I've picked the latter approach (cat /proc/meminfo), since it provides most detailed statistics. My question is, how do I accurately compute the amount of memory that can be successfully allocated by a process at a certain time?

My guess is, (MemFree + Buffers + Cached) is the maximum amount of memory that could be available for a new process (or a currently running one). Am I right?

Sincerely,
Onur

---

### Post by SOULRiDER on 2008-02-25
A process can also use swap, but swap is slow. If you find yourself using swap often then its sime to get more RAM. Everything that is buffers/cache can be replaced by your programs memory needs, and thats ok.

I personally like how htop shows memory usage.

---

### Post by blinkum on 2008-02-25
Thanks a lot for your reply, so I'll compute the amount of memory available for my process as:

MemFree + Buffers + Cached

Oh, forgot the mention, for performance purposes, the process can not use swap (actually there is not any swap partition for that reason).

I installed htop now, it has a nice display for the human eye, but I don't think it can be parsed well by a script. Is there a mode I'm missing?

---

### Post by SOULRiDER on 2008-02-25
If theres no swap partition i would suggets making one. Also, think aobut this, if theres no swap partition it means your programs dont need to use swap memory meaning that you have enough RAM. More RAM is always welcome and should speed things up a little by buffering/caching but theres also a limit on how much RAM you can use (depending on the processor you have, 32 or 64 bit).

---

### Post by blinkum on 2008-02-25
The Ubuntu box I have runs on a CF card, so if I enable a swap partition, it means frequent writes on that partition, which is not a desirable thing on a CF card.

---

### Post by andrewPCT on 2008-02-25
First off, it sounds as if the software you are running is horrible in terms of memory management.

Either way, why reboot the system when you could just end the process and restart it?

---

