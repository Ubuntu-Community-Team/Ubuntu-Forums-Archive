---
title: "memory management - out of memory errors"
date: 2008-09-08
forum: Apple Hardware Users
---

### Post by aws910 on 2008-09-08
Hi all, I have a problem that's really crippling my system.  Ubuntu won't use most of my main memory, and won't use any swap.  Programs are going slow and crashing.

output from free command:
```
             total       used       free     shared    buffers     cached
             total       used       free     shared    buffers     cached
Mem:       3088280    2426392     661888          0      37692    1816964
-/+ buffers/cache:     571736    2516544
Swap:      8193140          0    8193140

```

output from cat /proc/meminfo
```
MemTotal:      3088280 kB
MemFree:        489344 kB
Buffers:         32212 kB
Cached:        1748892 kB
SwapCached:          0 kB
Active:        1413216 kB
Inactive:      1026948 kB
HighTotal:     2208588 kB
HighFree:         3968 kB
LowTotal:       879692 kB
LowFree:        485376 kB
SwapTotal:     8193140 kB
SwapFree:      8193140 kB
Dirty:           66212 kB
Writeback:         148 kB
AnonPages:      659168 kB
Mapped:         706044 kB
Slab:            44528 kB
SReclaimable:    23704 kB
SUnreclaim:      20824 kB
PageTables:       3824 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   9737280 kB
Committed_AS:  1493152 kB
VmallocTotal:   114680 kB
VmallocUsed:     50604 kB
VmallocChunk:    61428 kB

```

I don't know much about memory management.  Sometimes I have to "fdisk -l" then "sudo swapon /dev/hda4" just to make the swap available, but even then the system won't use it.

---

