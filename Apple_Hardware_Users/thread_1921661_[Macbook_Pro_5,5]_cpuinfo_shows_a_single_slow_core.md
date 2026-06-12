---
title: "[Macbook Pro 5,5] cpuinfo shows a single slow core?"
date: 2012-02-07
forum: Apple Hardware Users
---

### Post by alfiejohn on 2012-02-07
Hi guys,

I've been on this Macbook Pro 5,5 for at least 2 years now, but only tonight did I think to have a look at /proc/cpuinfo. I was shocked to find:

  - Processor 0 was the only processor (even thought it's a Core2 Duo with HyperThreading)
  - CPU MHz is at 798 (it's 2.53Ghz, although it could be stepped down?)

I can see HyperThreading is in the flags, and `uname -a` shows that I'm running an SMP kernel. So my questions are:

  - Why isn't there 4 processor (since it's HT and a Core2 Duo) entries in /proc/cpuinfo
  - Why is the cpu running at 798Mhz
  - Why did it take me so long to notice this

Alfie

---

