---
title: "Laptop spawning processes after lid close."
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by Sambalbai on 2006-09-14
My laptop starts acting weirdly after closing the lid and opening it again. When I do so, the CPU usage shoots to 50% (it's a dual core, so 1 core gets maxed out) and the harddisk led starts blinking continuously. When I ran top, I couldn't discover a single process taking a lot of CPU time, so it looks like the system is spawning a lot of short-lived processes:

```
top - 22:44:51 up 28 min,  1 user,  load average: 0.57, 0.26, 0.26
Tasks: 129 total,   2 running, 127 sleeping,   0 stopped,   0 zombie
Cpu(s): 24.8% us, 24.4% sy,  0.0% ni, 49.8% id,  0.0% wa,  0.7% hi,  0.3% si
Mem:   1034460k total,   792992k used,   241468k free,    28600k buffers
Swap:  2216928k total,        0k used,  2216928k free,   557016k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5085 root      15   0 56624  38m 4556 S    2  3.9   1:06.79 Xorg
 5231 paul      15   0 31952  16m  12m S    1  1.6   0:03.46 kded
 5300 paul      15   0 32504  16m  12m S    1  1.6   0:04.36 konsole
 5301 paul      15   0 30536  17m  13m S    1  1.7   0:13.59 superkaramba
 4229 syslog    15   0  1764  688  564 S    0  0.1   0:00.07 syslogd
 4408 haldaemo  15   0  6884 5484 1564 S    0  0.5   0:01.90 hald
12524 paul      16   0  2196 1132  856 R    0  0.1   0:00.18 top
14717 root      22   0  2644 1312 1060 S    0  0.1   0:00.01 lid.sh
    1 root      16   0  1568  532  460 S    0  0.1   0:01.36 init
    2 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0
    5 root      RT   0     0    0    0 S    0  0.0   0:00.01 migration/1
    6 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1

``` 
I also found that if I close the lid for only a few seconds, the system gets back to normal again after a minute or so. Maybe something is queuing up when the lid is closed?

Any ideas what this could be? Thanks.

Configuration:
Asus A6T
kernel: 2.6.15-k7
OS: kubuntu 6.06

---

### Post by jchau on 2006-09-30
Your screensaver? Some of these have pretty intense animations.

---

### Post by Sambalbai on 2006-10-01
No, I had that disabled at the time. But in the meantime I found a workaround for this problem. I replaced klaptop with kpowersave. That seems to have fixed it. But thanks for thinking with me.

---

