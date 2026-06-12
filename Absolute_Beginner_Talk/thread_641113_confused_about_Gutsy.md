---
title: "confused about Gutsy"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by weiliang on 2007-12-15
Hello,

I just bought a new computer:

Intel core2 Quad 2.4GHz
Intel Desktop M/B DP35DP
Kingston Memory DDR2 PC-6400 1GB
SATA-2 250GB Seagate HDD
VGA GeForce 7200GS 256MB PCIe

I installed with **Gutsy Server Edition 64bit**.
The questions are:

Every time I booted up, the following message is appeared:
**[32.450192] PCI: Failed to allocate mem resource 06:20000@50000000 for 0000:01:00:0**
_Anything wrong with my hardware or Gutsy?_

Boot Process is stopped at message:
**Running Local Scripts (/etc/rc.local)         OK**
I should press ENTER to displaying login prompt. _Is it normal?_

Thanks advance for any help.

---

### Post by mahiyar on 2007-12-15
It might mean that whatever card is in the PCI slot, video card, lan or whatever is not being read properly, it might create problem it might not create problem.
 
As long as you can login I dont see any problems.

---

### Post by weiliang on 2007-12-15
Yes, I just discovered the problem, It's my GeForce VGA card. Since it's for server that doesn't need GUI, I think it's fine. Thanks.

How about my second question
> **weiliang said:**
> 
Boot Process is stopped at message:
**Running Local Scripts (/etc/rc.local)         OK**
I should press ENTER to displaying login prompt. _Is it normal?_

---

