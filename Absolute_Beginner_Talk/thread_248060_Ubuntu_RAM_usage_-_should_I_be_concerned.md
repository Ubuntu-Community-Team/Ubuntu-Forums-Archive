---
title: "Ubuntu RAM usage - should I be concerned?"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by Copps on 2006-08-31
Have been monitoring system load through the "top" command. The PC I'm using has 1GB of RAM installed. According to the output below (if I'm interpreting correctly), I only have about 20MB which is not being used ?

In terms of what I am running, one Firefox browser window, rhythmox, terminal and XGL. Anyhow, here's that top output. Any ideas?

top - 20:11:57 up  1:07,  2 users,  load average: 0.36, 0.69, 0.82
Tasks:  84 total,   1 running,  83 sleeping,   0 stopped,   0 zombie
Cpu(s): 14.8% us,  3.3% sy,  0.0% ni, 70.0% id, 11.0% wa,  0.4% hi,  0.5% si
Mem:   1036096k total,  1015004k used,    21092k free,     5868k buffers
Swap:  2096472k total,    18920k used,  2077552k free,   693356k cached

##########################################################
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4997 steve     15   0  107m  22m  13m S  8.0  2.2   2:13.91 rhythmbox
 4366 root      15   0  146m 123m 9552 S  2.0 12.2   4:51.43 Xgl
    1 root      16   0  1564  524  460 S  0.0  0.1   0:01.15 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.09 events/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 kblockd/0
    9 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  116 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  117 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  119 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  118 root      15   0     0    0    0 S  0.0  0.0   0:01.54 kswapd0
  706 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod
 1835 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 1935 root      15   0     0    0    0 S  0.0  0.0   0:00.01 kjournald
 2161 root      12  -4  2424  912  368 S  0.0  0.1   0:00.34 udevd
 2945 root      20   0     0    0    0 S  0.0  0.0   0:00.00 shpchpd_event
 2979 root      11  -5     0    0    0 S  0.0  0.0   0:00.01 kgameportd
 3406 dhcp      14  -2  2336  592  296 S  0.0  0.1   0:00.00 dhclient3
 3498 root      15   0     0    0    0 S  0.0  0.0   0:00.46 kjournald
 3889 root      16   0  2152 1192  644 S  0.0  0.1   0:00.00 acpid
 3979 syslog    16   0  1768  672  548 S  0.0  0.1   0:00.02 syslogd
 4005 root      16   0  1680  496  412 S  0.0  0.0   0:00.02 dd
 4007 klog      17   0  2400 1328  388 S  0.0  0.1   0:00.06 klogd
 4332 root      15   0 10908 1792 1220 S  0.0  0.2   0:00.00 gdm
 4338 root      16   0 11344 2632 1996 S  0.0  0.3   0:00.02 gdm
 4371 hplip     16   0 12868  920  696 S  0.0  0.1   0:00.00 hpiod
 4373 root      15   0 27904  13m 3676 S  0.0  1.4   0:11.96 Xorg
 4378 hplip     15   0  9408 4680 1100 S  0.0  0.5   0:00.01 python
##########################################################

---

### Post by Copps on 2006-08-31
Tasks:  84 total,   1 running,  83 sleeping,   0 stopped,   0 zombie
Cpu(s): 14.8% us,  3.3% sy,  0.0% ni, 70.0% id, 11.0% wa,  0.4% hi,  0.5% si
Mem:   1036096k total,  1015004k used,    21092k free,     5868k buffers
Swap:  2096472k total,    18920k used,  2077552k free,   693356k cached

---

### Post by IYY on 2006-08-31
Nothing to be concerned about, I think. Linux is designed to use the memory you throw at it, not impress people with how much of it is going to waste.

That is, unless you feel your system is running too slowly, in which case some application may be hogging the memory.

---

### Post by aysiu on 2006-08-31
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by az on 2006-08-31
> **Copps said:**
> Have been monitoring system load through the "top" command. The PC I'm using has 1GB of RAM installed. According to the output below (if I'm interpreting correctly), I only have about 20MB which is not being used ?


Ideally, you would only have about 1 meg not used.

Unused memory is wasted memory.

The kernel will decide which process' memory to dump when the time comes where something needs the ram.  Is that what you are worried about?

Linux handles ram a lot differently than windows.

---

### Post by Copps on 2006-08-31
That explains it perfectly. Just another Windows nuance that I've carried over since switching to Ubuntu last weekend.

```
steve@pc1:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1011        996         15          0          7        675
-/+ buffers/cache:        312        698
Swap:         2047         18       2028
```

Looks good to me, thanks all

---

