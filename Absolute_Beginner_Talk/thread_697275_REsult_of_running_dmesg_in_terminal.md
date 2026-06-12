---
title: "REsult of running dmesg in terminal"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by RoBo5050 on 2008-02-15
Hello forum members,
  
   This post is regarding a problem of an original ATI Radeon video card driver(installed with Ubuntu 7.10 that worked great until a recent analog modem install),but i found a similar thread in another post that I thought may help diagnose the ATI driver problem:
 
50.565790] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   51.357016] NET: Registered protocol family 10
[   51.357212] lo: Disabled Privacy Extensions
[   52.043064] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   52.043203] agpgart: Device is in legacy mode, falling back to 2.x
[   52.043299] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   52.043472] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   52.492296] [drm] Setting GART location based on new memory map
[   52.492355] [drm] writeback test succeeded in 1 usecs
[   53.421060] NET: Registered protocol family 17
[   63.006784] UDF-fs: No VRS found
[   63.147654] ISO 9660 Extensions: Microsoft Joliet Level 3
[   63.221206] ISO 9660 Extensions: RRIP_1991A
[   67.204494] eth0: no IPv6 routers present
[  832.594904] mtrr: no MTRR for f0000000,2000000 found
[  835.041583] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[  835.041607] agpgart: Device is in legacy mode, falling back to 2.x
[  835.041614] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  835.041695] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[  835.395499] [drm] Setting GART location based on new memory map
[  835.395558] [drm] writeback test succeeded in 1 usecs
[  881.157655] UDF-fs: No VRS found
[  881.190773] ISO 9660 Extensions: Microsoft Joliet Level 3
[  881.230320] ISO 9660 Extensions: RRIP_1991A
[ 1403.483570] mtrr: no MTRR for f0000000,2000000 found
[ 1403.756682] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[ 1403.756707] agpgart: Device is in legacy mode, falling back to 2.x
[ 1403.756714] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[ 1403.756794] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[ 1430.996979] mtrr: no MTRR for f0000000,2000000 found
[ 1431.269528] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[ 1431.269552] agpgart: Device is in legacy mode, falling back to 2.x
[ 1431.269559] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[ 1431.269640] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode

I would like to know if anyone knows what this log is telling me;it shows that
in more than one instance AGP video card is set at X4 speed,then falls back to X2,and the current driver only has one(1)resolution setting:600X460!!

If anyone knows where I can download a compatible ATI,Linux driver for my mobile Radeon AGP-interface card,I would greatly appreciate it!!

---

### Post by spiderbatdad on 2008-02-15
I saw a similar post recently. It seems like reinstalling the linux-restricted-modules solved the problem.

---

