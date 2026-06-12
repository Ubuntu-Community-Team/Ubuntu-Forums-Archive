---
title: "Problem with DSL on Ubuntu 7.04"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by sachill on 2007-06-15
Ive just updated from Ubuntu 5.04 to 7.04. On the old edition I could connect to the internet (DSL connection). Now, after doing the same network configurations I did then, I cant connect on 7.04   Each time I enable roaming mode, all the Connection Settings get greyed out and I cant select anything.  Please help.


I just ran ifconfig, and this is what I get:

eth0 Link encap:Ethernet HWaddr 00:08:74:9D:00:BD 
inet6 addr: fe80::208:74ff:fe9d:bd/64 Scope:Link 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets:40 errors:0 dropped:0 overruns:0 frame:0 
TX packets:121 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:14868 (14.5 KiB) TX bytes:23158 (22.6 KiB) 
Interrupt:11 Base address:0xec00 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:1336 errors:0 dropped:0 overruns:0 frame:0 
TX packets:1336 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:102928 (100.5 KiB) TX bytes:102928 (100.5 KiB)

---

### Post by aaron_summer on 2007-06-15
I ran into a simular problem when installing Ubuntu 7.04 on my laptop.

The atheros wifi was in roaming mode ...

This worked for me, I hope it helps.

```
ifconfig eth0 up
```

---

### Post by sachill on 2007-06-15
doesnt work:  it says

SIOCSIFFLAGS: Permission denied

---

### Post by sachill on 2007-06-15
PLEASE can someone help me...I REALLY need to get online...   :confused:

---

### Post by sachill on 2007-06-15
Im not sure why this is not working because it worked on ubuntu 5.04 this morning before I replaced it with 7.04      Please help me...

---

### Post by aaron_summer on 2007-06-15
Sorry,

Did you try

```
sudo ifconfig eth0 up
```

---

### Post by sachill on 2007-06-16
yes I did...still no luck  :(

---

### Post by sachill on 2007-06-16
Each ti,e I plug in the ethernet cable, on the top right of the screen it says 

¨You are now connected to the wired network¨

But then when I try to connect to a website, it says Server Not Found...

I really am begging you guys and girls to help me sort this out...:KS

---

