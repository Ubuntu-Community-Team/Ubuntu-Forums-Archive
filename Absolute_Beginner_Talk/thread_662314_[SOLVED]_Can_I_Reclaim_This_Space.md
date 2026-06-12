---
title: "[SOLVED] Can I Reclaim This Space?"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by perlluver on 2008-01-08
I was looking at my hard drive, and I just wanted to know If I can reclaim this extended space?

> Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23944   192330148+  83  Linux
/dev/sda2           23945       24321     3028252+   5  Extended
/dev/sda5           23945       24321     3028221   82  Linux swap / Solaris


---

### Post by blueridgedog on 2008-01-08
My read is that /dev/sda5 is inside the extended partition /dev/dsa2, so the short answer is no ie this looks normal.

---

### Post by perlluver on 2008-01-08
Thank you, just wanted to know.  I wasn't sure if that was right or not.

---

