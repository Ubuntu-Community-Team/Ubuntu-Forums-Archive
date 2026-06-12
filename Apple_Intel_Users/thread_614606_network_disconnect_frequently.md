---
title: "network disconnect frequently"
date: 2007-11-16
forum: Apple Intel Users
---

### Post by vincentzhu on 2007-11-16
Ubuntu 7.10, Macbook C2D (2GHz).

wired network disconnect frequently. After I click wired network, I can connect to the internet for just a few minutes.Then I was disconnected. So  i need to re-click wired network to re-connect to the internet.

However, if i choose wireless network, I was always connected to the internet. This is really weird as wired network should be better than wireless.

And I also ask other people who are using windows xp, they told me that they do not have this frequently disconnect problem. Besides, my mac os x system also do not have this problem.

Can anyone give some hint?

---

### Post by ukripper on 2007-11-16
Troubleshooting could be vast in your case. Let us start from your network cable - have you made sure your cable is fine? Try replacing it with another one and try again.

what you get when your wired connection is connected type following command and paste output here:
sudo ifconfig

---

### Post by vincentzhu on 2007-11-16
ath0      Link encap:Ethernet  HWaddr 00:1C:B3:BC:08:81  
          inet6 addr: fe80::21c:b3ff:febc:881/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:19:E3:43:FC:BF  
          inet addr:147.8.246.85  Bcast:147.8.246.255  Mask:255.255.255.0
          inet6 addr: fe80::219:e3ff:fe43:fcbf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3325 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4650402 (4.4 MB)  TX bytes:483478 (472.1 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-1C-B3-BC-08-81-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44310 errors:0 dropped:0 overruns:0 frame:918
          TX packets:677 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:3750922 (3.5 MB)  TX bytes:29222 (28.5 KB)
          Interrupt:16 


I think my cable is good, as the wired network is quite good under mac os x.



> **ukripper said:**
> Troubleshooting could be vast in your case. Let us start from your network cable - have you made sure your cable is fine? Try replacing it with another one and try again.

what you get when your wired connection is connected type following command and paste output here:
sudo ifconfig

---

### Post by ukripper on 2007-11-16
Are you using static address? or from DHCP?

---

### Post by cyberdork33 on 2007-11-16
> 147.8.246.85

That is a very odd IP address...

---

### Post by ukripper on 2007-11-16
> **cyberdork33 said:**
> That is a very odd IP address...

looks static to me

---

### Post by ukripper on 2007-11-16
can you ping your router?

---

### Post by vincentzhu on 2007-11-16
DHCP

> **ukripper said:**
> Are you using static address? or from DHCP?

---

### Post by vincentzhu on 2007-11-16
How to ping my router, thanks.

> **ukripper said:**
> can you ping your router?

---

### Post by cyberdork33 on 2007-11-16
> **vincentzhu said:**
> How to ping my router, thanks.
```
ping *ip.address.of.router*
```

repalcing 
[I]ip.address.of.router
[/I]with the actual ip address of your router.

---

### Post by vincentzhu on 2007-11-16
> **cyberdork33 said:**
> ```
ping *ip.address.of.router*
```

repalcing 
[I]ip.address.of.router
[/I]with the actual ip address of your router.



No timeout occured, really weird.  Does it mean  the network is ok now?

Besides, wiered network is good for the last two hours.

---

### Post by ukripper on 2007-11-16
timeout means your machine is not connecting to your router at that given instance.
it seems to me DHCP is not assigning correct ip address to your machine.
Can you connect via wireless and then paste output of following command:
```
sudo ifconfig
```

```
sudo iwconfig
```

---

### Post by tombott on 2007-12-14
I am getting the same issue here, but not on a Mac.
I have a Acer Aspire 9500 with a RTL-8169 Gigabit Ethernet and the LAN drops all the time.
I am an IT consultant and travel to different client sites on a daily basis. Sometimes the connection is fine,  other times it will drop every 5 minutes or so.
I have tried using Static or DHCP assigned addresses, but they both drop.
Wireless works without any problems, and I never had this issue with any previous versions of Ubuntu running on the same laptop.
The only thing I can think is the card may have issues auto detecting Link Speed and Duplex mode.
I know how to change this in Windows but have no idea in Ubuntu.
Any ideas?

Tom.

---

