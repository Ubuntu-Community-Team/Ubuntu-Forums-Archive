---
title: "Gusty BCM4306 problem"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by zhanglini on 2007-11-23
I wasn't planning on upgrading (or maybe downgrading) to Gibbon, but the other day my computer froze while I was using Feisty. SO I force-restarted (using the power button). After that I could not start Feisty any more because it gave me this GDM error message. SO I thought it was a good time to clean install Gibbon.
I did, now my wireless (bcm4306) connection is gone!!! I tried "restricted manager", but it kept telling me "bcmxxx is not enabled". It took me a month to get it to work under Feisty. NOw I have to start all over again.
Anyone can point me to the right direction ? --- fix bcm under Gibbon?  I have searched around and could not find anything.

---

### Post by spiderbatdad on 2007-11-23
[http://ubuntuforums.org/showthread.php?t=571188&highlight=troubleshooting+wireless](http://ubuntuforums.org/showthread.php?t=571188&highlight=troubleshooting+wireless)

---

### Post by CCNA_student on 2007-11-23
I also once had a wireless NIC from Broadcom and could not get it to work. What I did was I simply bought a new wireless Network card from Intel, the Intel 2915ABG for about $25. And once had that wireless NIC in my system it just worked.

---

### Post by zhanglini on 2007-11-24
> **spiderbatdad said:**
> [http://ubuntuforums.org/showthread.php?t=571188&highlight=troubleshooting+wireless](http://ubuntuforums.org/showthread.php?t=571188&highlight=troubleshooting+wireless)

I added multiverse, universe whatever to my repo and ran "restricted manager" again, this time I got the wireless card light on.  But still there is no connection.

In the thread you posted, it says the wireless should be wlan1 when you run "lshw -C network", but I have eth0.  Does this cause the problem?
Thanks

---

