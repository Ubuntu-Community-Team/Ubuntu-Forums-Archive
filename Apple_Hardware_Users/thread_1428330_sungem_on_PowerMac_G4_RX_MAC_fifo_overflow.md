---
title: "sungem on PowerMac G4: RX MAC fifo overflow"
date: 2010-03-12
forum: Apple Hardware Users
---

### Post by alexei.colin on 2010-03-12
Hi,

This is the same problem as in [this thread]("http://ubuntuforums.org/showthread.php?t=1324991"), but I cannot move that thread to the PPC section, so I'm starting a new one here (maybe a kind mod could move/combine as necessary, thanks in advance).

Machine: PowerMac G4 (no more firmware updates applicable)
System: Linux 2.6.31-19-powerpc #56-Ubuntu Thu Jan 28 00:50:48 UTC 2010 GNU/Linux
Ethernet: 0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth GMAC (Sun GEM) (rev 01)
Driver: sungem (srcversion: 9C4DDFB8D2201E852413F4F)

Issue: This gets written to the log periodically:
eht0: RX MAC fifo overflow smac[<a mem address>]
and if enough of those get written, then the system loses network connectivity. 

I wanted to say it started after I updated to 9.10 (different version of sungem), but in 2.6.28-6-powerpc (fewer) same error messages are still logged. I never witnessed loss of connectivity under the older kernel, but the error msg is there, period.
Edit: I did witness loss of connectivity under older kernel, but the reason could lie in some package update: I know, unlikely.. but I had no problems for weeks of uptime before. Maybe there was some hardware change in the network beyond my knowledge, who knows.

To bring back the network I can do:
ifdown eth0; rmmod sungem; modprobe sungem; ifup eth0
(I never tried without reloading the module)

There are very very few ancient and inconclusive references to the same problem on Google. [This thread]("http://forum.soft32.com/linux/NIC-kernel-error-ftopict308814.html") seems to imply that this was fixed in ~2.6.12, but I guess not.

Bottomline, if somebody knows where should I post this so that sungem maintainers could look at it, please reply. Thank you!

---

### Post by linuxopjemac on 2010-03-13
I would send your findings to Benjamin Herrenschmidt, he is involved in the PPC kernel.

benh at kernel.crashing.org

---

### Post by alexei.colin on 2010-03-21
linuxopjemac, thank you for referring to Ben. He replied and might look into it.

Meanwhile, I put the module reloading and interface restarting into a cron job that executes every hour: sudo crontab -e
```
# m h  dom mon dow   command
0  *  *   *   *     /usr/sbin/fix-sungem
```
and the script /usr/sbin/fix-sungem contains 
```
/sbin/ifdown eth0 && /sbin/rmmod sungem && /sbin/modprobe sungem && /sbin/ifup eth0
```
Script must be executable: chmod +x /usr/sbin/fix-sungem

---

