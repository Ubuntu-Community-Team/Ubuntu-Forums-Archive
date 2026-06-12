---
title: "Internet connection problem"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by ilunga on 2008-01-18
I have just installed unbuntu 7.10 and I can't connect to the internet. I followed the instructions given on how to connect but it did not work. My connection is wireless. Can anyone tell me what I have to do to get the wireless connection done?

Thanks for your help

Ilunga.

---

### Post by st33med on 2008-01-18
Could you post the output of this from the terminal:
```
ifconfig
```

The terminal is in Applications>>Accessories>>Terminal

---

### Post by abhuram on 2008-01-18
eth0      Link encap:Ethernet  HWaddr 00:14:22:9E:DD:30  
          inet addr:192.168.1.122  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fe9e:dd30/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63177 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30661 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20857985 (19.8 MB)  TX bytes:6521222 (6.2 MB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:13:CE:8D:60:8D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:903242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122932 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x2000 Memory:dfbfd000-dfbfdfff 

eth1:avah Link encap:Ethernet  HWaddr 00:13:CE:8D:60:8D  
          inet addr:169.254.7.152  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0x2000 Memory:dfbfd000-dfbfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9133 (8.9 KB)  TX bytes:9133 (8.9 KB)


this is what I got. I cannot connect to internet using wireless network. please help

---

### Post by Het Irv on 2008-01-18
Do you know what kind of Wireless card you have?
If you do not know post output of** lspci**

---

### Post by Xell Strider on 2008-01-18
You should check with the comman iwconfig in terminal, if there is an interface maybe the problem is with the parameters of the wireless interface(You can modify the settings in Network Settings).

---

