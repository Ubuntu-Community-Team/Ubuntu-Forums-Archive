---
title: "Won't connect to internet work on intel mac"
date: 2009-12-17
forum: Apple Hardware Users
---

### Post by PrincetonofPR on 2009-12-17
Well the title says it all, i just updated to 9.10 on my intel mac, dual-booting, and it wont connect to internet, wired or wireless. The model is 4,1.

---

### Post by chrisbuntu on 2009-12-17
I have a January 2006 intel 17inch imac.

My wired network connection worked fine.  When I first installed 9.10 I installed the proprietary drivers for the wireless immediately.  This prevented me from ever getting working wireless on that install.
I reinstalled 10.04 and did an upgrade before installing wireless- from then it worked perfectly.

Does your wired network work on OSX?

Chris

---

### Post by PrincetonofPR on 2010-01-03
well, yes it does work i have no idea, ill see to what i can do jeje

---

### Post by Gen2ly on 2010-01-04
What does 'ifconfig -a' show you?

---

### Post by linuxopjemac on 2010-01-04
you can try this:
[http://mac.linux.be/content/no-network-all-wired-and-wireless](http://mac.linux.be/content/no-network-all-wired-and-wireless)

---

### Post by phawnex on 2010-01-04
is it ur osx that the internet won't work?

or ubuntu?

---

### Post by PrincetonofPR on 2010-01-06
it wont work on ubuntu, on mac i works just fine. i was on vacations and erased the partitions for ubuntu i am now updating to 9.10 so ill post an update to tell u guys if it woks or not ;)

---

### Post by PrincetonofPR on 2010-01-07
ok so here is what i get when i put ifconfig - a with a ethernet cable connected to the mac. ummm so, i cant upgrade, firefox wont load any webpage. btw how do I do this? ([http://mac.linux.be/content/no-network-all-wired-and-wireless](http://mac.linux.be/content/no-network-all-wired-and-wireless)) xD thanks

eth0      Link encap:Ethernet  HWaddr 00:1f:f3:ce:ee:4e  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:f3ff:fece:ee4e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7577 (7.5 KB)  TX bytes:7774 (7.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pan0      Link encap:Ethernet  HWaddr 36:61:89:fb:94:27  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by phawnex on 2010-01-07
if not try this.

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

it helped me with my wireless.

---

### Post by PrincetonofPR on 2010-01-07
well, that made ubuntu recognize the airport card... hmmm maybe it's just my modem. It's a relic... like... 10 yrs. old xD ill check somewhere else to si if i get some internet acces to see if it works thanks anyway. ill post back so u know wahat hppened jeje

---

