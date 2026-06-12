---
title: "slow ubuntu?"
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by masooga on 2006-03-04
So I've been running Ubuntu for a little over a week now and I absolutely love it.  I wish there was a way I could contribute but I guess I'll have to wait until I become more familiar with the system.

Recently, however, my startup has been very slow once it starts loading my desktop.    Synaptic and Add Applications really slows down my computer so it borders on non-responsive.  Is there anything I can do to bring back speedy ubuntu?

---

### Post by John.Michael.Kane on 2006-03-04
you could add more mem. with out knowing your system spec's, and what you use it for. it will hard to tell the best way to fix your issue.

---

### Post by chimera on 2006-03-04
We'll have to know your system specs to help you more precisely, but I'd recommend you to use a lightweight desktop enviroment (like fluxbox or iceWM). Also, try running 

```

top

```

to determine which applications are taking up most of your CPu time, and see if you can safely shutdown any of them

---

### Post by masooga on 2006-03-04
hmasuga@Rilo:~$ top

top - 15:15:28 up 59 min,  2 users,  load average: 0.11, 0.29, 0.33
Tasks:  87 total,   3 running,  84 sleeping,   0 stopped,   0 zombie
Cpu(s):  8.9% us,  0.7% sy,  0.0% ni, 79.9% id,  9.4% wa,  0.9% hi,  0.2% si
Mem:   1036560k total,   471340k used,   565220k free,    22492k buffers
Swap:  3036244k total,        0k used,  3036244k free,   271748k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
    1 root      16   0  1560  528  460 S  0.0  0.1   0:01.74 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.09 events/0
    4 root      11  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  104 root      10  -5     0    0    0 S  0.0  0.0   0:00.06 kblockd/0
  132 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  133 root      15   0     0    0    0 S  0.0  0.0   0:00.03 pdflush
  135 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  134 root      25   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0
  722 root      15   0     0    0    0 S  0.0  0.0   0:00.02 kseriod
  949 root      10  -5     0    0    0 S  0.0  0.0   0:00.54 ata/0
  954 root      25   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
  958 root      15   0     0    0    0 S  0.0  0.0   0:00.17 scsi_eh_1
 1648 root      15   0     0    0    0 S  0.0  0.0   0:00.00 khubd
 2703 root      15   0     0    0    0 S  0.0  0.0   0:00.06 kjournald

The actual hardware should not be the problem, I've got a gig of ram and my processor is a Pentium M 750 (1.86GHz/533MHz FSB).

---

### Post by IYY on 2006-03-04
This is clearly a problem with Gnome or Metacity. If you don't mind losing your configuration, just reinstall it. Otherwise, try to troubleshoot:

Have you installed a new theme? Changed the fonts? Changed something else that could make it work slower?

Try adding a new account and logging in to it. Is it faster?

---

### Post by masooga on 2006-03-04
I think it was the post-it feature that I had put into the icontray.  Thank you though!

---

