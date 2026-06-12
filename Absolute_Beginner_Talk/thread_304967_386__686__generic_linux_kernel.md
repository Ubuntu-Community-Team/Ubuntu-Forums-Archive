---
title: "386 / 686 / generic linux kernel"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by IanVaughan on 2006-11-22
Ok, I've tried to understand this, posts say the 686 is obsolete, but I still think I am worse of with the "generic" 368 kernel.

This shows I have a 686 core, doesnt it?
```
ian@homer:~$ uname -rm
2.6.17-10-386 i686
```

I know that when I had Dapper on, and installed 686, I had two cpu graph lines on the System Monitor CPU history.
But now I cant get 686 installed correctly, I feel I am loosing out.
Any help?

---

### Post by o_fortuna on 2006-11-22
The development team did several tests comparing the -386 and -686/-k7 kernels. The difference was tiny and, in some cases, -386 outperformed -686. Thus, it was decided that, to save server space and bandwidth, Ubuntu would only compile their kernel for -386; that is the -generic kernel.

If you are desperate you could compile the kernel for -686 yourself, but that would be akin to jumping off a tall cliff head-first with no protective gear except a big rubber ball (ie crazy).

The -686 kernel is included for updates (if you had the -686 kernel installed in dapper and updated); it doesn't do anything now. You won't miss anything by installing the -generic kernel -- even SMP is enabled by default, so there's nothing to worry about. You will not notice an appreciable difference in performance.

---

### Post by IanVaughan on 2006-11-22
Ok thanks for that.
So just one small question then, do I want the generic or 386 modules?
(I like to only have what I use/need to understand more, so will remove what I dont)

2.6.17-10-386
or
2.6.17-10-generic

Cheers

---

### Post by kerry_s on 2006-11-22
It depends on what you need.
Do you have duel cpu?(you need smp->generic has it)
Are you using proprietary drivers?(everytime i install nvidia-glx it wants 386)

Etc....Without knowing your specs we can't recommend one or the other.

---

### Post by mirkov on 2007-11-15
what if you have both nvidia graphic card AND a dual core cpu?

with 386 kernel, only one core is active, nvidia-glx or nvidia-glx-new packages install only in -386 kernel. 

neither is really acceptable. i suppose one could remove restricted modules and install nvidia driver from nvidia's site, only it seems like a bit too much tinkering with a relatively common system these days.

---

