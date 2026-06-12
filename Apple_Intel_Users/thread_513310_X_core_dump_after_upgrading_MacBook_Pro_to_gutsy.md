---
title: "X core dump after upgrading MacBook Pro to gutsy"
date: 2007-07-30
forum: Apple Intel Users
---

### Post by dexem on 2007-07-30
Hi, I've upgraded my MacBook Pro to gutsy, and after the upgrade, I get a core dump each time I try to start X.

I get:

```

Backtrace:
0: X(xf86SigHandler+0x81) [0x80c8631]
1: [0xffffe420]
2: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0xb79a1b53]
3: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0xb799d1a1]
4: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxPreInit+0x988) [0xb7997a48]
5: X(InitOutput+0x9a4) [0x80a82f4]
6: X(main+0x27b) [0x8076c6b]
7: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d80040]
8: X(FontFileCompleteXLFD+0x1e5) [0x80761c1]

```

This is just after trying to find a correct modeline. I have been reading for hours about similar problems, but none gave me a correct bugfix. My xorg.conf is identical to another which is working on a Macbook pro with same hardware, so I'm thinking it's about some library problem...

I've "dpkg -P" all xserver and xorg packages and I've reinstalled them (also xserver-xorg-fglrx), so... I don't know what to do.
I'm not sure if it is a real bug, because the other laptop works... so I haven't opened a bug yet

Any ideas?

Thanks :)

---

### Post by cyberdork33 on 2007-07-30
I would file a bug, or confirm one that is already reported and post your information. There are already others with similar errors. I used to get something similar with Tribe 2 on my iMac, then a couple weeks later I tried booting again, and have not had the issue since.

---

