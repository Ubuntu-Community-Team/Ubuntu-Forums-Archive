---
title: "MacBook 2.2Ghz - Wireless please?"
date: 2008-01-18
forum: Apple Intel Users
---

### Post by WillJeffery on 2008-01-18
I'm using a MacBook 2.2Ghz (Gutsy 64 aswell) and I have a couple of questions...

How do I get my wireless working? I can't figure it out... What is my chipset? Is it Broadcom or Atheros? Or other? :confused:

Thanks!!

(I'm also a huge Ubuntu noob, so nothing too complicated please! I've only had ubuntu for 20 hours.)

---

### Post by tgalati4 on 2008-01-18
Please post the output of (from a terminal):

>lspci -v

and

>lsmod

---

### Post by cyberdork33 on 2008-01-18
or just tell us when you got the macbook. the newest have Broadcom, the older ones all have atheros.

---

### Post by WillJeffery on 2008-01-18
02:00.0 Network controller: **Broadcom** Corporation BCM4328 802.11a/b/g/n (rev 03)
        Subsystem: Apple Computer Inc. Unknown device 0088
        Flags: bus master, fast devsel, latency 0, IRQ 7
        Memory at 90500000 (64-bit, non-prefetchable) [size=16K]
        Memory at 90000000 (64-bit, prefetchable) [size=1M]
        Capabilities: <access denied>


I'm guessing I have Broadcom? Now what haha

---

### Post by cyberdork33 on 2008-01-20
You need to use ndiswrapper.  See the wiki page for Macbook Santa Rosa:
[https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-2f7056245889dcedf7dc1d286118bfda214af23b](https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-2f7056245889dcedf7dc1d286118bfda214af23b)

---

