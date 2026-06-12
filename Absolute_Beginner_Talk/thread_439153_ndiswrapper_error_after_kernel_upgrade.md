---
title: "ndiswrapper error after kernel upgrade"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Pulka on 2007-05-10
had everything working fine before new kernel. After the update, i get this error:

sudo modprobe ndiswrapper

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument


since ndiswrapper can't load, i don't have internet.

i'm running edgy.

anyone can help me?

---

### Post by Pulka on 2007-05-10
It doesn´t even recognize wlan0 anymore. But the driver seems to be ok. More information:


**ndiswrapper -l**

neti2220 : driver installed
        device (17FE:2220) present


**iwconfig**

lo        no wireless extensions.

eth0      no wireless extensions.



**ifconfig**

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:85:53:31  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:6 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

---

### Post by Pulka on 2007-05-10
anyone

---

### Post by Pulka on 2007-05-10
please

---

### Post by Acglaphotis on 2007-05-10
can you use the old kernel? if yes, does it works with it?

-Acgla

---

### Post by Pulka on 2007-05-10
i tryed just a while ago. It worked.

But after another restart, even the old kernel gives the error. When booting, i can see some errors about modprobe

---

### Post by Acglaphotis on 2007-05-10
Hummm... Try deleting the old kernel, and then see if there is any change. Whats is your wireless card anyway?

-Acgla

---

### Post by Pulka on 2007-05-10
how do i delete the old kernel?

Acer IPN2220 Wireless LAN Card

---

### Post by Acglaphotis on 2007-05-10
I ment delete the new kernel :rolleyes: . Anyway, do it from synaptic (system> administration > synaptic package manager) Search for it and delete the **new** kernel.

-Acgla

---

