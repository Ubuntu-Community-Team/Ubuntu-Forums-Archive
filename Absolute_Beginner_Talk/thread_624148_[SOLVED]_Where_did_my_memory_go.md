---
title: "[SOLVED] Where did my memory go?"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2007-11-26
I installed Xubuntu on a p3 800mhz with 256Mb Ram system... 
I was told that Xubuntu was the best *buntu to use because it only requires minimal system requirements.

But when I preform the top command it shows that pretty much all of my 256Mb of ram is already gone (except for a measly 4Mb)... where did it all go, I can't see the processes that are eating up all this memory?
Here is the top command results:
```

top - 17:56:17 up 18 min,  2 users,  load average: 0.13, 0.09, 0.19
Tasks: 106 total,   1 running, 104 sleeping,   0 stopped,   1 zombie
Cpu(s):  0.4%us,  0.4%sy,  0.0%ni, 99.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    255992k total,   251940k used,     4052k free,     7476k buffers
Swap:   746980k total,    34760k used,   712220k free,    97624k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5078 basskozz  15   0  2360 1152  876 R  0.4  0.5   0:00.06 top
    1 root      15   0  2948 1856  532 S  0.0  0.7   0:02.18 init
    2 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0
    4 root      34  19     0    0    0 S  0.0  0.0   0:00.01 ksoftirqd/0
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 events/0
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 khelper
   26 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0
   43 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kseriod
   72 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
   73 root      25   0     0    0    0 S  0.0  0.0   0:00.01 pdflush
   74 root      10  -5     0    0    0 S  0.0  0.0   0:00.09 kswapd0
  125 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
 1859 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0
 1860 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux
 1862 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
 1863 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1
 1865 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd
 1866 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 2133 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kjournald
 2339 root      20  -4  2960 1304  408 S  0.0  0.5   0:00.74 udevd
 3128 root      19  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused
 3259 root      18  -5     0    0    0 S  0.0  0.0   0:00.00 kgameportd
 3609 daemon    15   0  1812  504  412 S  0.0  0.2   0:00.00 portmap
 3628 statd     24   0  1876  712  616 S  0.0  0.3   0:00.00 rpc.statd
 3755 root      18   0  1696  520  448 S  0.0  0.2   0:00.00 getty
 3756 root      18   0  1692  512  448 S  0.0  0.2   0:00.00 getty
 3759 root      18   0  1696  520  448 S  0.0  0.2   0:00.00 getty
 3760 root      18   0  1696  520  448 S  0.0  0.2   0:00.00 getty
 3761 root      18   0  1692  516  448 S  0.0  0.2   0:00.00 getty
 3762 root      18   0  1692  512  448 S  0.0  0.2   0:00.00 getty
 3829 root      17  -5     0    0    0 S  0.0  0.0   0:00.00 kondemand/0
 3905 syslog    18   0  1916  696  564 S  0.0  0.3   0:00.12 syslogd
 3964 root      24   0  1832  532  444 S  0.0  0.2   0:00.04 dd
 3966 klog      18   0  2492 1396  408 S  0.0  0.5   0:00.14 klogd
 3987 messageb  15   0  2912 1048  756 S  0.0  0.4   0:00.18 dbus-daemon
 4003 root      15   0 12556 2024 1772 S  0.0  0.8   0:00.19 NetworkManager
 4017 root      15   0  3276 1280 1116 S  0.0  0.5   0:00.02 NetworkManagerD
 4030 root      25   0  3088  816  704 S  0.0  0.3   0:00.00 system-tools-ba
 4031 root      25   0  2776 1256 1092 S  0.0  0.5   0:00.00 dbus-daemon
 4050 haldaemo  15   0  5612 3632 2508 S  0.0  1.4   0:00.50 hald
 4051 root      25   0  3092 1012  880 S  0.0  0.4   0:00.00 hald-runner
 4094 haldaemo  16   0  2156  892  772 S  0.0  0.3   0:00.00 hald-addon-keyb
 4152 haldaemo  16   0  3264 1184 1036 S  0.0  0.5   0:00.01 hald-addon-stor
 4159 root      18   0  5280  992  652 S  0.0  0.4   0:00.00 sshd
 4242 root      18   0  5800 2156 1612 S  0.0  0.8   0:00.02 cupsd
 4373 root      25   0     0    0    0 S  0.0  0.0   0:00.00 lockd
 4374 root      12  -5     0    0    0 S  0.0  0.0   0:00.00 rpciod/0
 4378 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 nfsd4
 4379 root      25   0     0    0    0 S  0.0  0.0   0:00.00 nfsd
 4380 root      25   0     0    0    0 S  0.0  0.0   0:00.00 nfsd
 4381 root      25   0     0    0    0 S  0.0  0.0   0:00.00 nfsd

```

---

### Post by tribaal on 2007-11-26
See the link in my signature

Hope it helps you understand - Linux never wastes any RAM :)

- Trib'

---

### Post by BassKozz on 2007-11-26
> **tribaal said:**
> See the link in my signature

Hope it helps you understand - Linux never wastes any RAM :)

- Trib'
Still alittle confused...
This makes sense:
> The reason Linux uses so much memory for disk cache is because the RAM is wasted if it isn't used.
But I still don't understand where the memory is going...
here is 'free -m' results:```
             total       used       free     shared    buffers     cached
Mem:           249        245          4          0         13         96
-/+ buffers/cache:        135        114
Swap:          729         33        695

```

So if I am reading this right;
96Mb is cached (and available) and 4Mb is free, then 149Mb is being **used**, to total 249... but what is using 149Mb ?
Should'nt more be cached?  
I am not running alot of processes as you can see from the 'top' command in my previous post.

---

### Post by erm27 on 2007-11-26
Don't know if this is of any use. 

I see that you have 1 zombie process. That could be "wasting" ram. But I doubt it, it seems normal.

Here is mine for comparison. i have 1.5 gig/ram

             total       used       free     shared    buffers     cached
Mem:          1508       1091        417          0        135        569
-/+ buffers/cache:        386       1122

As you can see it's about the same 2/3's of my ram are in use. And I only have 112 process running vs your 104. I think it's the "smarter" way linux handles memory. Keeps the previous process loaded until the memory is cleared for another process to take it's place. Or if you recall the process, it loads faster, rather than reloading from HD.

Hope I'm right, 1
Hope it makes sense 2.

---

### Post by tribaal on 2007-11-28
```
       total       used       free     shared    buffers     cached
Mem:           249        245          4          0         13         96
-/+ buffers/cache:        135        114
Swap:          729         33        695
```

The way you read it is:

Out of 249 Mbs of RAM, 245 are used, and 4 are free.
Without the 96Mbs of cache, and 13 Mbs of buffers,
you would have 135 Mbs of RAM used and 114 Mbs of RAM free (114 = 4 + 96 + 13 + roundings).
Since buffers and cache have the lowest priority in memeory management, it gets automatically replaced by "useful" stuff when you start a new process.

:)

- Trib'

---

### Post by OrangeCrate on 2007-11-28
Very interesting trib', thanks for the explanation and link. This is a topic I never understood completely, but do now.

:)

---

### Post by tribaal on 2007-11-29
Glad I could help :)

- Trib'

---

