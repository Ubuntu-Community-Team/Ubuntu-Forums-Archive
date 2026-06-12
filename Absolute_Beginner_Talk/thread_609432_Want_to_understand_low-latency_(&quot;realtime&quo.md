---
title: "Want to understand low-latency (&quot;realtime&quot;)l vs &quot;regular&quot; kernel"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by wilberfan on 2007-11-10
After reading the cool stuff that Ubuntu Studio can do (audio and video apps, etc), I installed it.  I've messed around with it a bit--enough to determine that my sound card (Audigy SE) is not up to the task of running duplex with JACK, etc...

Here's my question:   If "low-latency" is a good thing--why isn't the "regular" Ubuntu running it?  If it's good for audio and video situations--is it BAD for other things?

What am I gaining and what (if anything) am I giving up by running a low-latency (realtime?) kernel?

---

### Post by tgalati4 on 2007-11-10
Mouse and keyboard response will suffer using a real-time kernel.  The real-time kernel is useful for a single-task workstation--editing or recording music for instance.

For multitasking in a desktop environment, you need a balance between keyboard/mouse response and CPU activity.  

Burn yourself a copy of Dynebolic and run it as a live disk, then try doing your normal desktop routine.  You will quickly see how the real-time kernel behaves.

---

### Post by wilberfan on 2007-11-11
Good to know...

My keyboard/mouse don't feel laggy at all running Gutsy Studio...   Could that be because I've got a reasonably fast system?  (AMD64x2)  If they were identically themed, etc, I'm not sure I could tell the difference if you sat me down at didn't tell me which one was booted, for example...

I don't play a lot of games--but would a gaming box be better off with a RT kernel?

---

### Post by dcstar on 2007-11-11
> **tgalati4 said:**
> Mouse and keyboard response will suffer using a real-time kernel.  The real-time kernel is useful for a single-task workstation--editing or recording music for instance.

For multitasking in a desktop environment, you need a balance between keyboard/mouse response and CPU activity.  

Burn yourself a copy of Dynebolic and run it as a live disk, then try doing your normal desktop routine.  You will quickly see how the real-time kernel behaves.

AFAIK the "rt" - or "low latency" kernels are the exact opposite to what you have said, they are optimised for more user response with higher interrupt settings and other kernel tweaks.

All kernels can be biased in various ways towards disk and/or process priority versus user I/O priority (versus many other things), and the "rt" kernels are biased towards Real Time response.

I have used standard kernels in the past, and even compiled my own Ubuntu kernels with the "CK" patches because they were better for users response when a system was also busy doing other things, but since Ubuntu made their versions of these available in the repositories I haven't needed to compile my own.

It is extremely simple to evaluate the difference, install both versions, boot up from them and test how well you keyboard/mouse respond when you are hammering your system with major work in the background - I find the "rt" version wins and I am quite happy to accept any minor loss of raw system throughput when using it.

---

