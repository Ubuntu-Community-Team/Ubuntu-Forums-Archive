---
title: "Dual Pentium Pro System -- how to tell?"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by Aero9000 on 2006-06-20
Hi all,

Amongst my computers I have a dual Pentium Pro system. It runs Xubuntu 6.06 and today I learned I could install the 686-kernel, which, in the Synaptic Package Manager, claims to support SMP (i.e. dual CPU). I installed the 686-kernel, but how can I tell my box dual CPU is acutally running off both CPUs?

Then, searching the forums, I learned I can also install something called "linux-686-smp", but that appears to install some documentation only.

I'll tell you one thing, the 686-kernel definitely runs a lot faster than the standard 386-kernel you get when you simply install from the live-CD. But still, I'd like some proof Xubuntu is now running both CPUs. Anyone? :confused: 

Thanks and best regards,
Maurice.

---

### Post by bollix47 on 2006-06-20
Open System Monitor and look under resources.

System - Administration - System Monitor

Does it show 2 cpu indicators?

---

### Post by taurus on 2006-06-20
Or from a terminal, type
```

cat /proc/cpuinfo

```

---

### Post by Aero9000 on 2006-06-20
Hi,

Since I'm running Xubuntu, unfortunately the System Monitor is not available. Running "cat /proc/cpuinfo" reveals I have two processors, so I guess Xubuntu is running on both CPUs. :D 

Interestingly enough though, although both CPUs are of the same stepping level (of course -- otherwise the box wouldn't be able to boot in the first place :rolleyes: ) the values for the bogomips for both CPUs are different. 399.98 and 398.93 respectively. The clock frequencies for both CPUs are identical: 199.463.

Well, I reckon I can just ignore that little discrepancy since the system runs perfectly stable.

Next step is to update the kernel on my Athlon 1800+ from 386 to k7....

Thanks again for your help,
Maurice.

---

