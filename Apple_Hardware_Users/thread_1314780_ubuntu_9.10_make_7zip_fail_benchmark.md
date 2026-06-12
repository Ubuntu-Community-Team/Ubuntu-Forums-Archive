---
title: "ubuntu 9.10 make 7zip fail benchmark"
date: 2009-11-04
forum: Apple Hardware Users
---

### Post by nelson.nazzicari on 2009-11-04
I just update from 9.4 to 9.10, I installed 7zip from software center and tryed to benchmark it.

It started in a good way but after a while it was killed abruptly.

Here the messages

```

7-Zip 9.04 beta  Copyright (c) 1999-2009 Igor Pavlov  2009-05-30
p7zip Version 9.04 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,8 CPUs)

RAM size:    1875 MB,  # CPU hardware threads:   8
RAM usage:   1701 MB,  # Benchmark threads:      8

Dict        Compressing          |        Decompressing
      Speed Usage    R/U Rating  |    Speed Usage    R/U Rating
       KB/s     %   MIPS   MIPS  |     KB/s     %   MIPS   MIPS

22:    8940   561   1550   8697  |   150120   776   1745  13539
23:   10161   568   1821  10353  |   146281   769   1740  13383
24:    9105   594   1649   9790  |   146462   775   1752  13585
Killed

```

I've looked at dmesg and here what I found

```
[28257.314326] Out of memory: kill process 776 (7z) score 459828 or a child
[28257.314356] Killed process 776 (7z)
[28257.314370] 7z: page allocation failure. order:0, mode:0x280da
[28257.314373] Pid: 776, comm: 7z Tainted: P   M       2.6.31-14-generic #48-Ubuntu
[28257.314376] Call Trace:
[28257.314385]  [<c056e41c>] ? printk+0x18/0x1c
[28257.314392]  [<c01b8310>] __alloc_pages_slowpath+0x340/0x480
[28257.314396]  [<c01b855f>] __alloc_pages_nodemask+0x10f/0x120
[28257.314400]  [<c01ca076>] do_anonymous_page+0x66/0x200
[28257.314404]  [<c012d3cd>] ? kmap_atomic_prot+0xcd/0xf0
[28257.314408]  [<c01cc460>] handle_mm_fault+0x330/0x380
[28257.314413]  [<c0572cf8>] do_page_fault+0x148/0x380
[28257.314417]  [<c0572bb0>] ? do_page_fault+0x0/0x380
[28257.314420]  [<c0570be3>] error_code+0x73/0x80
[28257.314422] Mem-Info:
[28257.314424] DMA per-cpu:
[28257.314426] CPU    0: hi:    0, btch:   1 usd:   0
[28257.314428] CPU    1: hi:    0, btch:   1 usd:   0
[28257.314431] CPU    2: hi:    0, btch:   1 usd:   0
[28257.314433] CPU    3: hi:    0, btch:   1 usd:   0
[28257.314435] CPU    4: hi:    0, btch:   1 usd:   0
[28257.314437] CPU    5: hi:    0, btch:   1 usd:   0
[28257.314439] CPU    6: hi:    0, btch:   1 usd:   0
[28257.314441] CPU    7: hi:    0, btch:   1 usd:   0
[28257.314443] Normal per-cpu:
[28257.314445] CPU    0: hi:  186, btch:  31 usd: 123
[28257.314447] CPU    1: hi:  186, btch:  31 usd: 142
[28257.314449] CPU    2: hi:  186, btch:  31 usd: 103
[28257.314452] CPU    3: hi:  186, btch:  31 usd:  26
[28257.314454] CPU    4: hi:  186, btch:  31 usd: 127
[28257.314456] CPU    5: hi:  186, btch:  31 usd: 158
[28257.314458] CPU    6: hi:  186, btch:  31 usd:  48
[28257.314460] CPU    7: hi:  186, btch:  31 usd:  80
[28257.314462] HighMem per-cpu:
[28257.314464] CPU    0: hi:  186, btch:  31 usd: 165
[28257.314466] CPU    1: hi:  186, btch:  31 usd:  73
[28257.314468] CPU    2: hi:  186, btch:  31 usd: 145
[28257.314470] CPU    3: hi:  186, btch:  31 usd: 165
[28257.314472] CPU    4: hi:  186, btch:  31 usd: 169
[28257.314474] CPU    5: hi:  186, btch:  31 usd: 156
[28257.314476] CPU    6: hi:  186, btch:  31 usd:  85
[28257.314479] CPU    7: hi:  186, btch:  31 usd: 171

```

(I hope to have spotted the important part. If something is missing please ask)

My machine is a 8 core mac pro 4.1 and I installed the 32 bit version

---

