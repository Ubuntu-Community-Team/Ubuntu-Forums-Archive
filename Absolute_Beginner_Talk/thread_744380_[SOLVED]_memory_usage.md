---
title: "[SOLVED] memory usage"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by Samurai Penguin on 2008-04-03
I ran       cat /proc/meminfo

why is memFree so small at only 80mb?

MemTotal:       515848 kB
MemFree:         80828 kB
Buffers:         12132 kB
Cached:         237684 kB
SwapCached:          0 kB
Active:         238028 kB
Inactive:       163788 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       515848 kB
LowFree:         80828 kB
SwapTotal:     1502036 kB
SwapFree:      1502036 kB
Dirty:             324 kB
Writeback:           0 kB
AnonPages:      152008 kB
Mapped:          57324 kB
Slab:            15184 kB
SReclaimable:     7584 kB
SUnreclaim:       7600 kB
PageTables:       1876 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   1759960 kB
Committed_AS:   487116 kB
VmallocTotal:   507896 kB
VmallocUsed:     26736 kB
VmallocChunk:   478708 kB

---

### Post by Tatty on 2008-04-03
linux usually leaves software loaded in RAM even after closing it.  It will free up the memory if it is requested by something else.  This means that it doesnt have to re-load an application into ram if you open it again shortly after closing... so it speeds things up a little.

So it might appear full when its not really

---

### Post by NightwishFan on 2008-04-03
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)
That should help a bit.

---

