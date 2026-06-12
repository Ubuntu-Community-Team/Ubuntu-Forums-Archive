---
title: "Limiting apt-get cache size"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Paulmd on 2007-10-19
Last night I was doing some routine maintenance, and had discovered that the cache used by apt-get was on the order of 4 gigabytes. EEK!  Cleaning the cache was a simple matter of

```
sudo apt-get autoclean
```

What I want to know, is there some way to manage or automatically limit the cache so it doesn't grow to be a disk hogging monster again?

My hard drive is only 20GB, so it's not like I want it to take up a quarter of my disk again.

---

### Post by runemaste644 on 2007-10-19
Just apt-get autoclean it often! There should be a way to give that directory a personal partition, but it is very complex.

---

### Post by por100pre1 on 2007-10-19
Open Synaptic. In Synaptic preferences theres a setting for deleting installed packages.

---

### Post by Paulmd on 2007-10-19
> **por100pre1 said:**
> Open Synaptic. In Synaptic preferences theres a setting for deleting installed packages.


It seems I have 3 options:

Never delete anything
Never save anything
Only delete if the package is no longer available


What I'm hoping for is an option like:

Cache up to X megabytes. Or N days. Or something approaching auto management. Even if it's in a config file somewhere.

So it behaves more like a cache should behave. So I don't have to remember to clean the cache out. :-|

Or should I put it down as a feature request for Hardy Heron?

---

### Post by por100pre1 on 2007-10-19
> **Paulmd said:**
> It seems I have 3 options:

Never delete anything
Never save anything
Only delete if the package is no longer available


What I'm hoping for is an option like:

Cache up to X megabytes. Or N days. Or something approaching auto management. Even if it's in a config file somewhere.

So it behaves more like a cache should behave. So I don't have to remember to clean the cache out. :-|

Or should I put it down as a feature request for Hardy Heron?

I think you should contact the [Synaptic developers]("http://www.nongnu.org/synaptic/contribute.html") directly, IMHO.

---

### Post by Paulmd on 2007-10-20
> **por100pre1 said:**
> I think you should contact the [Synaptic developers]("http://www.nongnu.org/synaptic/contribute.html") directly, IMHO.

Done.

---

