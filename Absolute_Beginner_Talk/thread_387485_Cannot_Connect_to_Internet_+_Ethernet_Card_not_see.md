---
title: "Cannot Connect to Internet + Ethernet Card not seen"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by carpola on 2007-03-18
Hey everybody,

So I'm brand new to Ubuntu and Linux in general and I have one major problem. I cannot 

connect to the Internet by way of broadband modem. I've read lots of tutorials online and the 

reason that seems to be stopping me is that when I go to Network Connections, my network 

connection (intel pro/100 ve network connection) is not one of the available choices. I'm running

 Ubuntu 6.06, I believe, if that helps at all. Please post back if you have any other questions 

regarding hardware/software information. Thanks a lot!

---

### Post by oilchangeguy on 2007-03-18
open a terminal and type lspci, and post the output.

---

### Post by Kobalt on 2007-03-18
Hello,

Could you please start by posting the output of the following command line : ```
ifconfig
```
Just to check if your ethernet card is actually not configured...
You might also want to try a newer version of Ubuntu, aka 6.10, if your hardware isn't supported by 6.06...

---

### Post by carpola on 2007-03-18
When I typed in lspci, I received this:

```
0000:00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub  Interface (rev 02)

0000:00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (re v 02)

0000:00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)

0000:00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)

0000:00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)

0000:00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)

0000:00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI  Controller (rev 02)

0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)

0000:00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface  Bridge (rev 02)

0000:00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Contro ller (rev 02)

0000:00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (re v 02)

0000:00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller ( rev 02)

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH 5R) AC'97 Audio Controller (rev 02)

0000:01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/Ge Force 6600 GT] (rev a2)

0000:02:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev  04)

0000:02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Cont roller (rev 02)
```



Ipconfig gave me this:
bush:ipconfig:command not found

---

### Post by oilchangeguy on 2007-03-18
from lspci your ethernet card is there. and the other command you were requested to check is ifconfig, not ipconfig.

---

### Post by carpola on 2007-03-18
shoot, you're right. i'm just used to the windows prompt command ipconfig. i'll go check now.

---

### Post by fanny on 2007-03-18
listen i had the same problem . i will try to guide you step by step , my english isnt so good so try to understand. 
first you need to type in the terminal: "sudo pppoeconf" ( without" "). if you already did it o.k.
if not ,say yes to all the questions , dont forget to type your user name and password correct.
if you see under : system >administration>networking "eth0" its o.k. your modem isnt importent now. 
come back and tell me whats new.

---

### Post by carpola on 2007-03-18
ifconfig:
```
lo        Link encap:Local Loopback

        
  inet addr:127.0.0.1  Mask:255.0.0.0

        
  inet6 addr: ::1/128 Scope:Host

        
  UP LOOPBACK RUNNING  MTU:16436  Metric:1

   
       RX packets:5 errors:0 dropped:0 overruns:0 frame:0

  
        TX packets:5 errors:0 dropped:0 overruns:0 carrier:0

      
    collisions:0 txqueuelen:0

         
 RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

```

---

### Post by carpola on 2007-03-18
When I type sudo pppoeconf, it gives me the error message: Sorry, no working ethernet card could be found.

Then, it continues to say that modconf could not be found.

What can I do now?

---

### Post by carpola on 2007-03-18
Anyone? I need to be able to get onto the Internet on Linux. Is there anything I can about this?

---

### Post by Kobalt on 2007-03-18
If you had searched the forum with your ethernet card label you'd have found it's only natively supported since Edgy. 
So as I wrote before, you should head towards downloading, burning and running the Ubuntu 6.10 LiveCD to check that out.

---

