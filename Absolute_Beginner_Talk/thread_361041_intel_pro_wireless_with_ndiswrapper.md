---
title: "intel pro wireless with ndiswrapper"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by ultracat on 2007-02-13
hi all, 

I´m brand new to Linux.  I put Edgy on my Dell Inspiron 6400 laptop.  It has an Intel Pro Wireless 3945 ABG wireless card.  I followed the instructions here:  WifiDocs/Driver/Ndiswrapper.   

I got this far ok:  When I run this: ¨ndiswrapper -l" in terminal I get this output:
netw39x5                driver installed, hardware present 

So, I believe that means ndiswrapper has done it&#347; thing.  Then I ran the following without getting any error messages:

sudo depmod -a
sudo modprobe ndiswrapper

Here´s where I´m stuck.  Now that all that is done, there is no wlan0 or anything when I run ifconfig or iwconfig.  I get no wireless extensions at all.  I tried rebooting after all this and still nothing shows up.  Here is the output when I run each:

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:15:C5:22:C6:89  
          inet addr:192.168.0.150  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe22:c689/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2263 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2056768 (1.9 MiB)  TX bytes:313738 (306.3 KiB)
          Interrupt:217 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.242.1  Bcast:172.16.242.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.136.1  Bcast:172.16.136.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.


What am I missing?   It took me hours to get this far.  Would someone mind walking me through it, keeping in mind I´m totally new to Linux?

Thanks a million in advance for any help you can offer!

---

### Post by Jussi01 on 2007-02-14
Hmmm - I dont understand, there is a native linux driver for the 3945, why are you using ndiswrapper? 

[http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

---

### Post by ultracat on 2007-02-21
Thanks, but I'm an 'absolute beginner'.  I read that page and the documentation talks all about building the driver, re-compiling the Kernel.  Is there an easy way?

---

### Post by Bachstelze on 2007-02-21
You certainly don't need to do anythling like that to get your card working. It it detected out of the box in Ubuntu. Run this in a terminal, does it output something ?

```
lsmod | grep ipw
```

---

### Post by Ziox on 2007-02-21
> **HymnToLife said:**
> You certainly don't need to do anythling like that to get your card working. It it detected out of the box in Ubuntu. Run this in a terminal, does it output something ?

```
lsmod | grep ipw
```

I'm having the same problem, and the code above produced the following:
```
~$ lsmod | grep ipw
ipw3945               124576  0 
ieee80211              35272  1 ipw3945
```

What does that mean? And is there a complete guide to installing the driver?

---

