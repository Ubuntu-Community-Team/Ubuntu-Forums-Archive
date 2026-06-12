---
title: "Dual Core Processors - Any Benefit?"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by az_human on 2006-08-29
Not that Ubuntu runs slow on my current Athlon XP 2400 (it runs pretty great actually... a LOT better than Windows XP), will it show any out-of-the-box benefits in speed from running on a dual core processor?  What about the applications?

I assume I would need to download the SMP kernel for a dual core chip?

Do applications benefit from this, or just the kernel?

Thanks for any input!

---

### Post by jdong on 2006-08-29
Look at your computer first. Put a few system monitors on your taskbar. When your computer feels slow, what's being fully utilized? If your answer is CPU, then yes,  faster or more CPU's may give you a performance boost.

If the CPU usage is not full and your hard drive is grinding away, then you might want to go for better/faster hard drives or a RAID setup.

---

### Post by telegramsam on 2006-08-29
Do you need SMP for dual core?  I thought SMP was just for dual processor...?  (I'm asking, not advising...)  ;)

---

### Post by jdong on 2006-08-29
Yes, you need an SMP capable kernel in order for Ubuntu to utilize more than one CPU, regardless of whether they're physical processors or cores on one physical CPU chip.

In Ubuntu Dapper, all but the -386 kernel are SMP.

---

### Post by fluffnik on 2006-08-29
> **az_human said:**
> 
Do applications benefit from this, or just the kernel?

Do you run many concurrent processes?

Only multi-threaded apps will directly benefit dual (core) processors, but if you're multitasking dual procs will half the amount of context switching and the associated overheads.

My desktop machine is a dual PIII 750MHz and it's really snappy - compared to, say, an Athcanlon XP2400 - because it *can* do two things at once.

...of course all the grunty computation is done by headless Athcanlon XP2400 boxes in a cupboard...

An SMP machine is like a big V8; it just goes when you poke it and is never caught flat footed, off boost and in the wrong gear.

A turbo-nutter I4 uniprocessor machine of the same *total* power will be more easily caught out and prone to bogging down, but if you keep it in the groove it will just fly.

Maxing your RAM out is almost always better value than upgrading processors.

---

### Post by fluffnik on 2006-08-29
> **telegramsam said:**
> Do you need SMP for dual core?  I thought SMP was just for dual processor...?  (I'm asking, not advising...)  ;)

Multicore processors are effectively SMP on a chip, they present exactly the same problems as a similar number of discreet unicore processors.

Folks like Sun and IBM have been building 8 and 16 core processors for a while.

---

