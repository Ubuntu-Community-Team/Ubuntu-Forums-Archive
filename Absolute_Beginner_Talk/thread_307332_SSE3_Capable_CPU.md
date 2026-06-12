---
title: "SSE3 Capable CPU?"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-11-26
I'm trying to load a copy of OSX on vmware and the tutorial is advising 
to make sure my cpu is SSE2 or SSE3 capable. It gives me a windows program 
to download, but I couldn't find anything for Linux. Know of such a tool for
linux?

---

### Post by zgornel on 2006-11-26
> **shanepardue said:**
> I'm trying to load a copy of OSX on vmware and the tutorial is advising 
to make sure my cpu is SSE2 or SSE3 capable. It gives me a windows program 
to download, but I couldn't find anything for Linux. Know of such a tool for
linux? *cat /proc/cpuinfo |grep sse* - it should display a line with the instruction sets supported by the cpu (among other)

---

### Post by shanepardue on 2006-11-26
awesome! thank you very much!!

---

