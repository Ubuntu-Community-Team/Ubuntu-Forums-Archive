---
title: "Quick Kernel Question"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by sherpah on 2006-08-11
I am running Ubuntu on a Fujitsu lifebook p5000 - which has a a Pentium Mobile 900mhz process - part of a centrino setup, which also include onboard Wifi and Intel 855gm video card. What kernel should I be using? 386 or 686 and why?

my current uname -a:

Linux 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux



thanks

---

### Post by jordilin on 2006-08-11
It's a pentium class, then I would use the 686. If it has hyperthreading, then 686-smp

---

### Post by arjun.shankar on 2006-08-11
There were issues with the 686 kernel, and it seems they were resolved. You might want to take a look at these bugreports in detail before going in:

[https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/30570](https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/30570)

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30557](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30557)

I myself, haven't yet used the 686 kernel yet. I think I will get it myself in a few days, when I get some free time. I really don't like packages though. Will probably compile from the debian sources, and switch to vanilla if I find that problem.

---

