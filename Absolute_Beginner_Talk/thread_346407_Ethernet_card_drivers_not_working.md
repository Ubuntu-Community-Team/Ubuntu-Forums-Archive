---
title: "Ethernet card drivers not working"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by simon303 on 2007-01-25
After I installed Ubuntu 6.10 Edgy my ethernet card stopped working
It is a Belkin card based on the Realtek RTL8139 chipset
The drivers exist on the system and are 8139too but the system does not recognise the card
Is there anyway of 'reminding' the system the drivers exist and where the drivers are?
Thanks

---

### Post by chippy99 on 2007-01-25
If you type ***sudo lsmod*** does it list 8139cp and 8139too ?

If not you could try ***sudo modprobe 8139cp***

---

### Post by simon303 on 2007-01-26
***lsmod*** lists 8139cp and 8139too, but it says nothing is using them
***modprobe 8139cp*** does nothing i can see

---

### Post by chippy99 on 2007-01-26
What does output of ***sudo ifconfig*** look like, it should list device eth0 something like this ..

```
eth0      Link encap:Ethernet  HWaddr 00:02:44:B5:51:FA  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST NOTRAILERS RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1556 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1606 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1070332 (1.0 Mb)  TX bytes:244434 (238.7 Kb)
          Interrupt:11 Base address:0xd400 
```

---

### Post by simon303 on 2007-02-01
***ifconfig*** just shows a local loopback
no mention of my ethernet card
nothing like the above

---

