---
title: "wireless configuration Gutsy,  an improvement would be appreciated."
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by darkservlist on 2008-03-03
I would really appreciate any help with this issue i have, my wireless adapter is a wusb54g v4. I've already installed and seems to be working fine, but there must be something wrong with it, since this is what i get from my ifconfig command 


lo        Link encap:Local Loopback  
          inet addr x.x.x.x  Mask x.x.x.x
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2665 (2.6 KB)  TX bytes:2665 (2.6 KB)

rausb0    Link encap:Ethernet  HWaddr xx. xx . xx
          inet addr x.x.x.x  Bcast x.x.x.x  Mask  x.x.x.x
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:143279 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122278 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:146725379 (139.9 MB)  TX bytes:27314976 (26.0 MB)


as you can see the wireless is identified as Ethernet and the name given is rausb0 also this is how my interfaces file looks like 


# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
iface rausb0 inet dhcp
wireless-key xxxxxxxxxx
wireless-essid xxxxxxxxxx

auto rausb0


I'm not really sure what to add, or what to remove, I would like to be able to setup a static ip address but with this configuration I don't think that would be likely, 

Thanks in advance.

---

### Post by darkservlist on 2008-03-03
also i forgot to mention that the connection from time to time suddenly drops, and to get it going again I do the comm **sudo /etc/init.d/interfaces restart**.

---

