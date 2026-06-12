---
title: "Sambas speed is weird."
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2006-07-19
!!HELP!!
This is driving me mad:
Why is sambas rate fluctuating on a 100Mb Lan with no other activity.

It seems to fluctuate in pulses and when it gets to 0.0 the files being copied just freeze until it starts moving again??

I only want to copy a few gigs accross and at this rate it will take all night!! Sometimes it flatlines for so long windows gives up and thinks the connection has been dropped.

:confused:


This line in smb.conf is in there as advised but it made no difference
```
   
You may want to add the following on a Linux system:

   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192 IPTOS_LOWDELAY

```

---

