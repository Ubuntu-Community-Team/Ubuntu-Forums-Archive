---
title: "Setting up internet connection"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by yaki2007 on 2007-07-09
Hello 2 all ubuntu users!
Need some help!
I'm new to ubuntu, linux.
How can I set up my internet connection.
I have a cable modem, my ethernet card get's IP from it.
I can't understand where to set up my ISP name or IP address
I've tried this command:
"pppoeconf"
As I understand it should be asking me for a username and password, but it didn't
It's found my ethernet card, and then nothnig...
From other questions I read that the wired connection should be set  on roaming, I did so and still the same thing.
Can anybody explain it to me please

---

### Post by Taliskerd on 2007-07-09
If you type 'ifconfig' in a terminal, what output do you get?
(eth0 should be your ethernet card, so read off that section [lo is 'loopback', i.e your computer])

---

### Post by loserboy on 2007-07-09
1.is it a wired or wireless connection?

2. what version of ubuntu are you using

Most of the time internet works out of the box, are you sure everything is connected properly and that the hardware works?

if so go to the panel at the top left and click
System>Administration>Networking*  and you should see some infor about your card and other things, then let me know what you see

* it's called networking in version 6.10 (edgy), I think it might be called something else in feisty



EDIT: Taliskerd knows what he's doing, listen to him not me

---

### Post by yaki2007 on 2007-07-10
> **Taliskerd said:**
> If you type 'ifconfig' in a terminal, what output do you get?
(eth0 should be your ethernet card, so read off that section [lo is 'loopback', i.e your computer])

This is the output that I get:
Below I also print the output from windows
So I'm waiting for your reply

eth0   Link encap:Ethernet  HWaddr 00:11:09:DB:A4:AB   
          inet addr:172.21.167.52  Bcast:255.255.255.255  Mask:255.255.224.0 
          inet6 addr: fe80::211:9ff:fedb:a4ab/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:11368 (11.1 KiB)  TX bytes:2502 (2.4 KiB) 
          Interrupt:19 Base address:0xe200  

lo       Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b) 

================================================
Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 172.21.163.73
        Subnet Mask . . . . . . . . . . . : 255.255.224.0
        Default Gateway . . . . . . . . . : 172.21.160.1

PPP adapter Cable Connect:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 89.139.91.15
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 89.139.91.15

---

