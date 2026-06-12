---
title: "Where is my memory RAM?"
date: 2013-06-01
forum: Any Other OS
---

### Post by manolomanolo on 2013-06-01
Hi to all.

Similar problem here. I have 4GB installed but only 2.9GB of those are recognized by the system.

```
free -b -h
                  total       used       free     shared    buffers     cached
Mem:          2,9G       2,7G       160M         0B       121M       546M
-/+ buffers/cache:       2,1G       827M
Swap:         3,7G       1,3G       2,4G

```

Looking in the BIOS, just 64MB of the RAM is reserved to video card.
So, where's the missing 1GB?

I'm on Linux Mint 14 **64bit**
Kernel: 3.5.0-31-generic

---

### Post by Perfect Storm on 2013-06-01
**Moved to Other OS/Distro Support.**

---

### Post by trent.josephsen on 2013-06-01
Does the problem appear only on Linux? The simplest possibility is just an unseated RAM board. Even if you haven't physically messed with it recently sometimes ordinary vibrations can cause a loose module to go from working to not-working. If you've upgraded recently, maybe one of the modules was bad.

---

### Post by prodigy_ on 2013-06-01
> **manolomanolo said:**
> **64bit**
Are you sure? Use ```
uname -mpi
``` to check.

---

