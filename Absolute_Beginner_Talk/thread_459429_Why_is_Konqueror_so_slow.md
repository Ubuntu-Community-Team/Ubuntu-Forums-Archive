---
title: "Why is Konqueror so slow?"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by cknight on 2007-05-30
Right, so I heard that Konqueror is supposed to be one of the faster browsers on Linux.  But on my machine (running Kubuntu) Firefox (v 2.0.0.3) is loading sites about twice as fast as Konqueror (v 3.5.5).  Browsing with Konqueror is rather painful at the moment.  Any ideas why or how I might improve Konqueror's load time?

---

### Post by Crafty Kisses on 2007-05-30
Hmmm, go into your terminal and type:
```
top
```
Let's see if something is taking up a lot of resources. :p

---

### Post by Feba on 2007-05-30
Do you use FasterFox?

---

### Post by cknight on 2007-05-30
Part of the problem may have been that I had IPV6 disabled in firefox.  Adding the following line to /etc/environment seems to have improved Konqueror, but I'm still finding occasional pages that take a lot longer to load.

```
KDE_NO_IPV6=TRUE
```

The problem seems to be that Konqueror hangs (e.g. loading image 17 of 20, where it will sit for several seconds).

Here's my top output

```
top - 00:23:36 up 15 min,  1 user,  load average: 0.98, 1.20, 0.98
Tasks: 100 total,   1 running,  98 sleeping,   0 stopped,   1 zombie
Cpu(s): 27.8%us,  4.0%sy,  0.0%ni, 67.9%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:    514916k total,   501044k used,    13872k free,    72796k buffers
Swap:  1124508k total,        0k used,  1124508k free,   271896k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 3845 root      15   0 92548  20m 3964 S 16.1  4.1   1:25.66 Xorg
 4412 cknight   15   0 32416  15m  12m S 15.1  3.1   0:07.72 konsole
 4303 cknight   15   0 29152  13m  10m S  0.7  2.6   0:04.70 kwin
 4352 cknight   15   0  145m  49m  23m S  0.3  9.8   1:36.91 firefox-bin
 4757 cknight   15   0  2244 1136  844 R  0.3  0.2   0:02.45 top
    1 root      16   0  1632  540  448 S  0.0  0.1   0:01.87 init
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.22 ksoftirqd/0
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 events/0
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 khelper
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.05 kblockd/0
   10 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   11 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify
   69 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod
  100 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  101 root      15   0     0    0    0 S  0.0  0.0   0:00.04 pdflush
  102 root      15   0     0    0    0 S  0.0  0.0   0:00.11 kswapd0

```

Not yet tried Fasterfox, but I'll check it out.  Heh heh, don't suppose there is a FasterKonqueor?

---

