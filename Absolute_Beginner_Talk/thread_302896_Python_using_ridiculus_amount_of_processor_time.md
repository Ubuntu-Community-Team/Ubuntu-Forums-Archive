---
title: "Python using ridiculus amount of processor time"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by guitarist549 on 2006-11-19
I get this when running top>

top - 11:39:41 up 11:46,  2 users,  load average: 0.44, 0.63, 0.72
Tasks: 125 total,   2 running, 123 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.5% us,  1.0% sy,  0.0% ni, 95.9% id,  0.2% wa,  0.2% hi,  0.3% si
Mem:   1033124k total,   506004k used,   527120k free,    12320k buffers
Swap:  3028212k total,    19992k used,  3008220k free,   160920k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4778 root      15   0 46360  35m  10m S    2  3.5   8:18.55 Xorg
 5552 ross      15   0 55308  40m  11m R    2  4.1  14:30.20 python
17031 ross      15   0 32808  13m 8436 S    1  1.3   0:01.42 gnome-terminal
 5423 ross      15   0 45340  20m  12m S    1  2.0   1:59.36 gaim
17053 ross      16   0  2204 1068  828 R    1  0.1   0:00.18 top
 5410 ross      15   0 68256  29m  15m S    0  3.0   0:41.09 gnome-panel
 5494 ross      15   0 58812 9216 7780 S    0  0.9   0:00.12 evolution-alarm
16974 ross      15   0  137m  41m  19m S    0  4.1   0:17.39 firefox-bin
    1 root      16   0  1568  460  396 S    0  0.0   0:01.23 init
    2 root      RT   0     0    0    0 S    0  0.0   0:00.03 migration/0
    3 root      34  19     0    0    0 S    0  0.0   0:00.27 ksoftirqd/0
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0
    5 root      RT   0     0    0    0 S    0  0.0   0:00.02 migration/1
    6 root      34  19     0    0    0 S    0  0.0   0:00.03 ksoftirqd/1
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1
    8 root      10  -5     0    0    0 S    0  0.0   0:00.28 events/0
    9 root      10  -5     0    0    0 S    0  0.0   0:00.06 events/1

Why is python hogging everything up? My computer is acting fairly sluggish now.. gah.

---

### Post by kosmic on 2006-11-19
The first thing you should do is to check what Python applications are you running.

For example applications like Gdesklets and other like that.

---

