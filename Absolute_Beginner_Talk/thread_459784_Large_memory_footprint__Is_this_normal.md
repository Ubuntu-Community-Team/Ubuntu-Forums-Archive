---
title: "Large memory footprint?  Is this normal?"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by cknight on 2007-05-31
Firstly, let me say that it is very possible that I don't fully understand what I'm looking at.  Here's the deal... Looking at 'top' in the terminal, I see 465Mb of memory used of 515 Mb total memory available.  The thing is, all I had running at that time was the shell/Konsole program (e.g. this being the only program I opened after a normal boot).  

This strikes me as an excessive amount of memory to use without having anything of consequence open and running.  Is it normal for the operating system to use this much memory?  If its relevant, I'm using Kubuntu Edgy.

Here's the output from top:
```
top - 06:57:39 up  6:49,  1 user,  load average: 0.26, 0.27, 0.23
Tasks:  90 total,   1 running,  89 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.6%us,  0.3%sy,  0.0%ni, 97.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    514916k total,   465028k used,    49888k free,    77984k buffers
Swap:  1124508k total,        0k used,  1124508k free,   274460k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 3845 root      16   0 90552  19m 3392 S  1.0  3.8   3:56.28 Xorg
 4412 cknight   15   0 32416  15m  12m S  1.0  3.1   0:09.76 konsole
 5186 cknight   16   0  2244 1124  844 R  0.7  0.2   0:00.29 top
    1 root      16   0  1632  540  448 S  0.0  0.1   0:01.87 init
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.22 ksoftirqd/0
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.05 events/0
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 khelper
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.05 kblockd/0
   10 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   11 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify
   69 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod
  100 root      15   0     0    0    0 S  0.0  0.0   0:00.01 pdflush
  101 root      15   0     0    0    0 S  0.0  0.0   0:00.04 pdflush
  102 root      15   0     0    0    0 S  0.0  0.0   0:00.13 kswapd0
  103 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
 1671 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 1721 root      10  -5     0    0    0 S  0.0  0.0   0:00.18 kjournald
 1794 root      15   0  1600  548  468 S  0.0  0.1   0:00.01 logd
 1940 root      12  -4  2604 1036  360 S  0.0  0.2   0:00.84 udevd
 2688 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 shpchpd
 2714 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused
 2736 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kgameportd
 3152 root      10  -5     0    0    0 S  0.0  0.0   0:00.21 kjournald
 3475 root      16   0  1600  504  432 S  0.0  0.1   0:00.00 getty
 3476 root      16   0  1596  504  432 S  0.0  0.1   0:00.00 getty
 3477 root      16   0  1596  504  432 S  0.0  0.1   0:00.00 getty
 3478 root      16   0  1596  504  432 S  0.0  0.1   0:00.00 getty
 3479 root      16   0  1600  508  432 S  0.0  0.1   0:00.00 getty

```

---

### Post by NikoC on 2007-05-31
```
Mem:    514748k total,   442404k used,    72344k free,    25220k buffers

```

I hadn't noticed it before, but that is indeed quite a large number! Any ideas anyone?

---

### Post by aysiu on 2007-05-31
Read this:
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by BaffledMollusc on 2007-05-31
Linux treats memory differently from what you might be used to from, say, Windows. 

As far as Linux is concerned, if there's free memory it's being wasted. After all, there's no point in having memory if you're not using it, right? So what it does it keep a lot of stuff buffered. For example, if you open an application, and then exit it, it keeps the application in memory, provided there's still space.

So even if you're not using many applications at any point in time, your RAM is filled with past applications along with other guesses of the Linux kernel about what you'll need next. That way, when you start up a new app, it'll be much faster as it won't have to load it from disk. Of course, if you keep opening more and more applications Linux will throw old stuff out of memory to make room for the stuff you really need now.

Rather than using "top", a good command is "free". So, for example, when I run "free" I get
```

             total       used       free     shared    buffers     cached
Mem:       1035412     961824      73588          0      26872     520836
-/+ buffers/cache:     414116     621296
Swap:      1485972       5268    1480704

```
According to the first line, I'm using 960MB out of 1GB. But if you look at the second line, you'll see I am actually only using 414MB - the rest is just cached stuff linux has pulled in because there's RAM available and it's guessing I'll need it soon.

---

### Post by cknight on 2007-05-31
Thanks for the great replies!  Makes sense.  For the record, here's my 'free' output:
```
             total       used       free     shared    buffers     cached
Mem:        514916     502512      12404          0      82088     281372
-/+ buffers/cache:     139052     375864
Swap:      1124508          0    1124508

```

As you can see, I'm only actually using ~140Mb which sounds about right.  Thanks again!

---

### Post by BaffledMollusc on 2007-05-31
Edit: Oops, ignore.

---

### Post by NikoC on 2007-06-01
> **aysiu said:**
> Read this:
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

That link cleared things up, thanks!

---

