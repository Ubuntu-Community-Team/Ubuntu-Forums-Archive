---
title: "cpu processes problem"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by oscar78 on 2007-04-27
I have a core 2 duo on my new machine and typically run simulations on them.  Usually, when no other large processes are running in the background, I can run two independent simulations (one on each of the processors), each one occupying close to 100% of an individual cpu capacity (as viewed from my system monitor).  

Today, however, each simulation is running on only about 50% of each individual processor capacity, and I dont seem to be running any other consuming processes in the background.   I would restart the computer and try again, but would like to avoid having to start my simulations all over again.  

Does anyone have a clue as to why the processes tab in the system monitor show only my two simulations, running only at half cpu capacity, yet the resources tab says each of my processors are running at full capacity?

---

### Post by 5-HT on 2007-04-28
I believe the CPU utilization on the processes tab reflects total processor usage and not that of the individual cores.

---

