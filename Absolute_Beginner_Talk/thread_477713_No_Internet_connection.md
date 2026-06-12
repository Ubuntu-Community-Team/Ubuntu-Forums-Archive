---
title: "No Internet connection"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by rex66 on 2007-06-18
I am trying to set up my brother's PC with ubuntu. He lives nearby me and uses the same isp (Time Warner)...Ubuntu had no trouble at all recognizing my ancient cable modem and connecting to the net. It appears it does not recognize his (unless it is another problem completely) ....he had a Motorola Surfboard SBV5220.  Anyone else ran into a problem like this that they were able to solve?

Thanks

rex

---

### Post by meborc on 2007-06-18
what is the output of "ifconfig" in the terminal?

what happens if you type "sudo dhclient"?

---

### Post by rex66 on 2007-06-18
meborc 

 I'm back at work now...but I will try these and post the results later....thank you

---

### Post by meborc on 2007-06-18
no problem... the command "ifconfig" should give you an output similar to mine:> eth0      Link encap:Ethernet  HWaddr 00:13:8F:CF:68:1A  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25810 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34823 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20042627 (19.1 MiB)  TX bytes:3429703 (3.2 MiB)
          Interrupt:17 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


the **lo** part is of no interest to you... the **eth0** part on the other hand shows that your network card is recognised and configured - a.k.a. this is what you want to see

---

### Post by shavenlunatic on 2007-06-18
USB or ethernet?

---

