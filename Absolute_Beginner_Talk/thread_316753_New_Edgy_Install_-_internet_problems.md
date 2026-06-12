---
title: "New Edgy Install - internet problems"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by gazza67 on 2006-12-11
Hi Everyone,

I have just installed Edgy, most stuff seems to work however I have one problem. My internet connection - I cant browse the internet. I  open up Firefox but it can only open local documents.

Strangly I open up a terminal session and type ping microsoft.com 
or any other site I can think of and it resolves the IP address so i presume that means at some level i am getting traffic to and from the net.

I have a very basic setup - an ethernet card connected directly to an adsl router. The router does seem to be giving me an address via DHCP.

Any help would be much appreciated.

Cheers,

 Gary

---

### Post by Kobalt on 2006-12-11
Hello,
Can you post us the result of the following command line : 
```
ifconfig
```

---

### Post by gazza67 on 2006-12-11
Here is the output from ifconfig

gary@gary-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:45:4A:B0  
          inet addr:10.1.1.2  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20c:6eff:fe45:4ab0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1956 (1.9 KiB)  TX bytes:2400 (2.3 KiB)
          Interrupt:209 Base address:0x9800 

eth1      Link encap:Ethernet  HWaddr 00:50:BF:E6:6C:7B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

gary@gary-desktop:~$

---

### Post by gazza67 on 2006-12-12
I have finally found the answer. It seems that I need to disable IPV6 in firefox via about:config


Gary

---

### Post by hyper_ch on 2006-12-12
hehehe, why does everyone ping micrsoft.com ?

I do normally the same for checking the connection

strange, ff should run with ipv6...

---

