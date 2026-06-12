---
title: "dual processor problem"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by bob_barker on 2007-03-26
i recently installed Ubuntu on my Dell Latitude D820, currently it only recognizes processor 0.  Does anyone have any idea why it doesn't recognize my second processor, ie processor 1 ?

If i run uname -a it gives me this:

2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

Thanks

Bob

---

### Post by 67GTA on 2007-04-06
What version of Ubuntu did you install? If it was 6.06 Dapper, then you need to install the i686 smp kernel instead of the generic smp kernel. Post the output from cat /proc/cpuinfo. Also check the system monitor in SYSTEM>ADMINISTRATION>system monitor and see if two cpu's are showing.

---

