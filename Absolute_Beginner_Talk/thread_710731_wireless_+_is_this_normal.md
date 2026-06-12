---
title: "wireless + is this normal?"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by myddewji13 on 2008-02-28
Hi,

I can (for some reason) connect to a wpa enterprise network without authentication... and then use it to connect to the internet etc....after about 5 min the connection stops working... now...if i try to connect using the following settings:
[http://www.it.ubc.ca/internet/wireless/wpa/wirelesswpaother.html](http://www.it.ubc.ca/internet/wireless/wpa/wirelesswpaother.html)

It lets me...but again the connection just stops working .(note the connection isnt dropped....it still shows up as connected at x%... the internet just stops working)..


so any ideas/help?

---

### Post by gimfred on 2008-02-29
Okay mate, we'll need to know what hardware you have. 

What brand  your wireless Access Point?

What brand is your modem?

What is the result of:

```
lspci | grep Ethernet
```

```
ifconfig
```?

---

### Post by myddewji13 on 2008-02-29
myd@myd-laptop:~$ lspci | grep Ethernet
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
myd@myd-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:72:43:92:2A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:177 errors:0 dropped:0 overruns:0 frame:0
          TX packets:177 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17596 (17.1 KB)  TX bytes:17596 (17.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1A:73:D0:FD:40  
          inet addr:128.189.201.144  Bcast:128.189.203.255  Mask:255.255.252.0
          inet6 addr: fe80::21a:73ff:fed0:fd40/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8291 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6678 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9087728 (8.6 MB)  TX bytes:879297 (858.6 KB)
          Interrupt:19 Memory:f4300000-f4304000 

myd@myd-laptop:~$

---

### Post by gimfred on 2008-03-15
I've lost my train of thought where I was heading with this one, can anyone else help myddewji13?

---

### Post by Fin_Bhera on 2008-03-15
Hey,

I'm not knowledgeable enough to help too much, but in my experience ditching NetworkManager in favour of WICD [http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/") is a quick fix to a lot of wireless problems.

---

### Post by myddewji13 on 2008-03-15
tried that....completely screwed everything up... went back to network manager...atleast i have internet now...dont worry about it..ill see if the problem is still present w/ hardy (cuz thats supposedly fixes my sound issues).... and if it is will repopen the thread...thanks for the help guys..

---

