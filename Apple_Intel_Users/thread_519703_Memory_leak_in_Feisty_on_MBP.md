---
title: "Memory leak in Feisty on MBP?"
date: 2007-08-07
forum: Apple Intel Users
---

### Post by CPUFreak91 on 2007-08-07
I'm running Kubuntu Feisty natively on a 15" 2nd Gen Macbook Pro. Recently I've been out of memory a few hours after booting up. Programs like Firefox and beagle were using up over 1700MB of memory (and I only have 2GB) and my system was running at a crawl. This didn't use to happen before. Beagle was using a lot of CPU recently, but I think that may be because it was scanning my home folder.

Here's a peek at what free -m would report when my system would slow down.
:```
 -/+ buffers/cache:        1858       161
```:


I haven't recently upgraded a kernel or any system libraries. I'm running the fglrx drivers and occasionally I use XGL and Beryl (but I haven't since the memory leak started). I do not have a swap partition/image.

---

### Post by cyberdork33 on 2007-08-07
> **CPUFreak91 said:**
> I do not have a swap partition/image.
I would guess that is the biggest issue, although I am unsure what is eating up the memory. You can use
```
ps -A
```to list the running processes, and try to 'killall *processname*' to figure out what the culprit is.

---

### Post by CPUFreak91 on 2007-08-08
Hmm. Well it looks like I'll just have to stop using Beagle and FF and look to alternatives. I stopped running them for the past two days and haven't had a memory problem. Thanks for the ps -A tip.

---

