---
title: "xserver not starting"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by shankru85 on 2007-07-28
Hi guys... i have been using ubuntu for the past 6 months or so... it had not given trouble so far... But suddenly when one fine day i start ubuntu, Xserver doesnt start.... When i manually tried to start X server, it gave the following error :confused:

Log file:"/var/log/Xorg/0/log"
config file:"/etc/X11/Xorg.conf"
1810(0):No video BIOS modes for chosen depth
Screen(s) found, but none have usable configuration.
Fatal server error
no screens found

XIO:fatal IO error 104(connection reset by peer) on Xserver ":0.0" after 0 requests (0 known processed) with 0 events remaining.

---

### Post by mkoehler on 2007-07-28
Hi,

Have you been playing around with the configuration settings within xorg.conf?  If so, you might try restoring the file:

```
cp /etc/X11/xorg.conf~ /etc/X11/xorg.conf
```

Also, if you could paste the contents of the log file here, that would be helpful for further debugging.

Cheers!

---

