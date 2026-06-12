---
title: "Good Battery only lasts 1hr MBP 2,1 [Lucid Lynx 10.04]"
date: 2010-06-19
forum: Apple Hardware Users
---

### Post by coolaj86 on 2010-06-19
I've got a 17" MacBookPro2,1 with a brand new battery which is only lasting me about an hour in Ubuntu.

In OS X the battery life is about 2:30, maybe 3 (quite short of the 4 or 5 I was hoping for from the new battery).


I haven't seen mention in the docs of any sort of special utility or instructions to turn on more power savings. Is this normal?



On the plus side, it seems to run the fan less often and generally be less hot than in OS X - and you would think that increased battery life would accompany that sort of positive change.

---

### Post by linuxopjemac on 2010-06-20
You could start with adding CPU monitoring panels in the top for both cores and to set the CPU performance to PowerSave. I also turned off bluetooth at boot:

add the following line to /etc/rc.local

```
rfkill block bluetooth
```

I dim the screen brightness to around 50%, that also helps

---

