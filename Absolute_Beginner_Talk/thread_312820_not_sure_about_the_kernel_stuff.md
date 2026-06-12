---
title: "not sure about the kernel stuff"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2006-12-05
I just installed the 64 bit version of 6.06 onto my laptop 
when I do a uname -a i get Linux WindowsSucks 2.6.15-27-amd64-generic #1 SMP PREEMPT Sat Sep 16 01:50:50 UTC 2006 x86_64 GNU/Linux


Does that sound right to you and how do I know if both processors are working???

---

### Post by yabbadabbadont on 2006-12-05
That looks correct.  The fact that it is showing SMP tells you that it is the mulitprocessor version of the kernel.  Just for fun, run:

cat /proc/cpuinfo

---

### Post by testbenchdude on 2006-12-05
Hmm. Here's a snippet of the output of cat /proc/cpuinfo for me:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping        : 6
cpu MHz         : 2400.112
cache size      : 4096 KB
physical id     : 1
siblings        : 1
core id         : 255
cpu cores       : 1

Shouldn't it show two cores? Does Linux not utilize both cores for a reason? Curious.

---

### Post by yabbadabbadont on 2006-12-05
Not sure if it would or not.  (I don't have an SMP machine :()  Right after bootup, you might try running "dmesg|less" and look at the kernel output at the start of the boot process.  I believe it should show how many CPUs/cores it has detected.

Edit: by the way, you might want to "man less" if you don't know how to use the less program.

---

