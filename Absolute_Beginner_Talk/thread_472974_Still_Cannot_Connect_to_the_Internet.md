---
title: "Still Cannot Connect to the Internet"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Wally Paulnuts on 2007-06-13
Anyone who can help would be greatly appreciated 

so this is the output when i do an ifconfig -a

eth0 Link encap:Ethernet HWaddr 00:02:A5:1E:CC:95
inet addr:192.168.1.15 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::202:a5ff:fe1e:cc95/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:468 (468.0 b)

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:738 errors:0 dropped:0 overruns:0 frame:0
TX packets:738 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:59140 (57.7 KiB) TX bytes:59140 (57.7 KiB)


I am unable to Ping the router, the destination is unreachable.

---

### Post by Sparkster185 on 2007-06-13
If you do a "lspci -v" is your Ethernet card recognized?

I run into a problem with my latop where if the ethernet is not plugged in when the OS wakes up (either from a reboot or wake up from suspend), it won't recognize it.  It's gotta be plugged in before the PC comes to life (for me at least).

---

### Post by willl on 2007-06-13
are you using dhcp or is that a static ip that you've configured? are you sure your router is at 192.168.1.1 and not 192.168.0.1?

---

### Post by Wally Paulnuts on 2007-06-13
its set for a static IP, yes my router is located at 192.168.1.1 as i can ping it from my dell windows laptop

---

### Post by lazyart on 2007-06-13
good time for a```
sudo ifdown eth0
sudo ifup eth0
```

Oh wait, you're static... any reason why you're static?  And is another device on the network trying to use the same address?

---

### Post by Wally Paulnuts on 2007-06-13
not that i know of...should i be set as dhcp instead of static?

---

### Post by lazyart on 2007-06-13
makes life easier as dhcp.

---

### Post by Wally Paulnuts on 2007-06-13
oh here is what i got when i put in the sudo commands

anthony@anthony-desktop:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
anthony@anthony-desktop:~$ sudo ifup eth0
anthony@anthony-desktop:~$

---

### Post by lazyart on 2007-06-13
Change to dchp if you havent yet, then post ifconfig -a again.

---

### Post by Wally Paulnuts on 2007-06-13
Here is the ifconfig a results

eth0      Link encap:Ethernet  HWaddr 00:02:A5:1E:CC:95  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0:avah Link encap:Ethernet  HWaddr 00:02:A5:1E:CC:95  
          inet addr:169.254.7.192  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5296 (5.1 KiB)  TX bytes:5296 (5.1 KiB)

---

