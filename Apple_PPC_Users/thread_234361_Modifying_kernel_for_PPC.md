---
title: "Modifying kernel for PPC"
date: 2006-08-11
forum: Apple PPC Users
---

### Post by discosammy on 2006-08-11
I'm not sure where to start, but i've search google and linux forums and haven't been able to find a clear answer.

i see all sorts of tweaks for "real-time" kernels in x86 forums.

would those work if I tried them on a PPC kernel?

I understand it's important to select the right kernel source, but beyond that, could I follow any kernel fixing tutorial as long as i modifying device and path names where appropriate?

from what i can find, it seems possible because some have tried. Has anyone succeeded? Is there any truth to a real-time kernel being distributed in the near future?

---

### Post by rasec on 2006-08-11
Why do you need a real-time kernel for? Unless you have an embedded system, I don't see why you would need it.

I checked the realtime-preempt patch for the 2.6.17 kernel and it looks like it supports the powerpc. You can get the patch [here]("http://people.redhat.com/mingo/realtime-preempt/patch-2.6.17-rt8"). I believe that it patches against the stock 2.6.17 kernel, not the latest stable version 2.6.17.8. To compile the kernel, just follow the x86 guides, but make sure that you use the pmac32_defconfig as your base config and you should be set.

---

### Post by ireneshusband on 2006-08-11
[INDENT]Why do you need a real-time kernel for? Unless you have an embedded system, I don't see why you would need it.[/INDENT]

A realtime kernel is useful for low-latency audio processing.

---

### Post by tidris on 2006-08-11
I have rtai installed on my G5 but I haven't tried to do anything with it yet. It is one of the packages available via the Synaptic Package Manager.

---

