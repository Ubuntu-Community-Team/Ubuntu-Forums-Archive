---
title: "Help with wired Internet connection"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by b21bballer on 2007-10-05
Output of ```
lspci | grep "Ethernet controller\|Network controller"
```

```
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

---

### Post by myk.dinis on 2007-10-09
What's seems to be the problem?  More information is always more helpful...

What's your question?

---

### Post by strabes on 2007-10-09
I have the exact same two network cards and both work perfectly out of the box. I bet you have a dell inspiron laptop.

---

### Post by b21bballer on 2007-10-09
> **strabes said:**
> I have the exact same two network cards and both work perfectly out of the box. I bet you have a dell inspiron laptop.

Yes.

I'm asking how to get this wired connection to work.

---

### Post by OffAxis on 2007-10-09
what does 

**ifconfig**

give you?

---

### Post by b21bballer on 2007-10-09
> **OffAxis said:**
> what does 

**ifconfig**

give you?

I get this:

```
eth0      Link encap:Ethernet  HWaddr 00:15:C5:25:02:1C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 

eth1      Link encap:Ethernet  HWaddr 00:13:02:C2:0B:E6  
          inet addr:192.168.200.250  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fec2:be6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1861 errors:0 dropped:301 overruns:0 frame:0
          TX packets:1860 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1696130 (1.6 MiB)  TX bytes:276120 (269.6 KiB)
          Interrupt:16 Base address:0x4000 Memory:dfdff000-dfdfffff 

eth0:avah Link encap:Ethernet  HWaddr 00:15:C5:25:02:1C  
          inet addr:169.254.2.163  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5204 (5.0 KiB)  TX bytes:5204 (5.0 KiB)
```

---

