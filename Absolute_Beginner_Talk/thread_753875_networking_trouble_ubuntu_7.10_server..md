---
title: "networking trouble: ubuntu 7.10 server."
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by e1ektrob0y on 2008-04-13
i just installed 7.10 server and the install would hang at "scanning the mirror". I tried unplugging the cable but it didnt work...Anyway, i installed with the cable unplugged and it worked but now i have no eth0 and no internet. Is there a command i can run to install the device? I have tried 
```
/etc/init.d/sudo networking restart 
```
and 
```
sudo dpkg-reconfigure dhcp3
``` but to no avail...can someone help me please? thanks...

p.s i can't even ping the router...

---

### Post by m_atif on 2008-04-13
Can you please post more information, especially network card info. Can be due to NIC driver issues. What does ifconfig -a give? Also can you give output of lspci?
Also check /etc/iftab

---

### Post by e1ektrob0y on 2008-04-13
> **m_atif said:**
> Can you please post more information, especially network card info. Can be due to NIC driver issues. What does ifconfig -a give? Also can you give output of lspci?
Also check /etc/iftab

ifconfig (without the -a) shows 
```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

ifconfig -a shows 

```

eth0    Link encap:Ethernet  HWaddr 00:14:85:21:21:DD  
          BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          


``` 
lspci shows up the intel onboard nic too.

---

### Post by wormser on 2008-04-13
I am not sure whats going on but here is a bump and something to try.  It looks like you are not getting an IP address via DHCP.

```
sudo dhclient
``` 

Update:

I just installed server and ran into the same issue.  I set up a static IP during the install and that did not help.  When I logged into the server I ran sudo dhclient eth0 and to my surprise it worked.  On the reboot the static IP settings took over.  Hopefully this works for you.

---

