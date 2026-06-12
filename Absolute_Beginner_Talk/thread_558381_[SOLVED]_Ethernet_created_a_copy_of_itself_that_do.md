---
title: "[SOLVED] Ethernet created a copy of itself that doesn't work?"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by weezerisrock on 2007-09-23
Ok so everything was working great on my ubuntu box.  I decided to give a small partition to windows in order to play a few games that are unplayable in linux.  I changed my partitions using gparted, installed windows, resetup my grub and everything was working fine.... So I thought.

IFCONFIG:
```
eth0      Link encap:Ethernet  HWaddr 00:01:80:3F:B9:6E  
          inet6 addr: fe80::201:80ff:fe3f:b96e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 

eth0:avah Link encap:Ethernet  HWaddr 00:01:80:3F:B9:6E  
          inet addr:169.254.6.201  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2493 (2.4 KiB)  TX bytes:2493 (2.4 KiB)
```

When I am in linux my onboard network card is dead in the water, no lights on the card, my router doesn't acknowledge the connection nothing.  That eth0: avah is new I think.  Its the same mac address as the eth0.  I'm not sure whats going on so I am asking stronger linux minds than mine to help me out.  As I said, this all happened after I completed my windows setup and resetup the grub.  The network card works fine in Windows XP.

Any help on this would be greatly appriciated.

---

### Post by weezerisrock on 2007-09-24
bump for some love?

---

### Post by raul_ on 2007-09-24
Maybe it's this

[http://en.wikipedia.org/wiki/Avahi_%28software%29]("http://en.wikipedia.org/wiki/Avahi_%28software%29")

It's just a suggestion though

---

### Post by weezerisrock on 2007-09-24
Hmm that gives me something to look at.  


Any help is greatly appricated raul_!  so thank you for taking the time to respond!  I'll be reading that sheet and I'll let you know if I find an answer.  If anyone else has anything to add please do!

---

### Post by weezerisrock on 2007-09-24
Ok I think I'm going about this the wrong way,  I double checked the settings on my laptop and they are the same, and the lan port on my laptop works.

So let me re-ask this question.  My internet is not working on my computer however it works fine on the windows partition.  The windows partition is new and my lan was working fine in Linux before I installed windows and resetup grub.  What information do you need from me in order to help me troubleshoot?

Thanks and please help!

---

### Post by weezerisrock on 2007-09-25
Ok I'm gonna mark this thread as solved and reopen it as another thread, since technically the subject of the thread has kinda been solved.

---

