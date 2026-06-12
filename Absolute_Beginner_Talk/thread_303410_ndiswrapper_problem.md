---
title: "ndiswrapper problem"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by WardLoockx on 2006-11-20
I'm trying to install my wireless card but it fails. when I try to scan for lists I get this error

when using
```
iwlist scan
```

I get
```
wlan0     Failed to read scan data : Resource temporarily unavailable

```

I used my linksys WUSB drivers (the inf file) and it says: device up ..... So thats ok I think

---

### Post by MrCheese on 2006-11-20
I had a wifi card which used ndiswrapper as there was no decent native driver - it worked ok-ish but was never all that stable. In the end I gave it all up & bought a natively supported card for a tenner from eBay (Atheros chipset based). You really can't go wrong with a kernel-supported card, rather than wrestling with unexplained drop-outs. 
Of course if you have built-in wifi that may not be an option for you.

---

