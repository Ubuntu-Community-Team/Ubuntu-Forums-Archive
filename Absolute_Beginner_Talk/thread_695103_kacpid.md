---
title: "kacpid"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by brandonhon on 2008-02-12
After installing Gusty on my laptop I have noticed a daemon named kacpid taking up a lot of cpu usage. It seems to only happen when the fan turns on. However when it does kick in it really eats up the cpu resources. Here is a capture of top. Does anyone have any idea what kacpid is exactly and why it eats up the cpu?

> 
PID USER   PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
33 root      11  -5     0    0    0 R           88  0.0 350:56.38 kacpid        39;49m
 1  root      15   0  2948 1852  532 S     0  0.1   0:01.42 init               39;49m
 2  root      10  -5     0    0    0 S    0     0.0   0:00.00 kthreadd           39;49m
 3  root      RT  -5     0    0    0 S    0      0.0   0:00.00 migration/0        39;49m
 4  root      34  19     0    0    0 S    0     0.0   0:00.86 ksoftirqd/0        39;49m
 5  root      RT  -5     0    0    0 S    0      0.0   0:00.00 watchdog/0         39;49m
 6  root      RT  -5     0    0    0 S    0      0.0   0:00.00 migration/1        39;49m
 7  root      34  19     0    0    0 S    0     0.0   0:00.03 ksoftirqd/1        39;49m
 8  root      RT  -5     0    0    0 S    0      0.0   0:00.00 watchdog/1         39;49m
 9  root      10  -5     0    0    0 S    0      0.0   0:00.37 events/0           39;49m
10 root      10  -5     0    0    0 S    0      0.0   0:00.01 events/1           39;49m
11 root      16  -5     0    0    0 S    0      0.0   0:00.00 khelper            39;49m
31 root      10  -5     0    0    0 S    0      0.0   0:00.01 kblockd/0          39;49m
32 root      10  -5     0    0    0 S    0      0.0   0:00.00 kblockd/1          39;49m
34 root      10  -5     0    0    0 S    0      0.0   0:00.03 kacpi_notify       39;49m
140 root    10  -5     0    0    0 S    0      0.0   0:00.01 kseriod           39;49m
168 root    20   0     0    0    0 S    0      0.0   0:00.00 pdflush           39;49m

---

### Post by brandonhon on 2008-02-14
Anyone? This process is eating up 85 - 95% of my cpu and i cannot kill it. Please someone help?

---

