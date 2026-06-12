---
title: "Setting up wireless connection on livecd"
date: 2008-02-15
forum: Apple Intel Users
---

### Post by Luc484 on 2008-02-15
Hi guys! I'm trying ubuntu for the first time. Seems great! Everything seems to work fine, the last time I had to set up Gentoo Linux on a laptop I had big troubles.

The only problem I'm having is with my wireless connection. I read many how to, and it seems to work fine, ifconfig sees my wireless device ath0 and the network manager sees all my wireless networks. Unfortunately, I simply can't connect. I'm now writing from cable network:

```
ubuntu@ubuntu:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:1B:63:00:EC:37  
          inet addr:192.168.0.15  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:418 errors:0 dropped:0 overruns:0 frame:0
          TX packets:326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:521123 (508.9 KB)  TX bytes:51199 (49.9 KB)

eth0      Link encap:Ethernet  HWaddr 00:19:E3:37:C5:E7  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:e3ff:fe37:c5e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4300 (4.1 KB)  TX bytes:12400 (12.1 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17445 (17.0 KB)  TX bytes:17445 (17.0 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1B-63-00-EC-37-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9753 errors:0 dropped:0 overruns:0 frame:17
          TX packets:755 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1114293 (1.0 MB)  TX bytes:80623 (78.7 KB)
          Interrupt:16
```

and this is the output of iwconfig:

```
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:8354  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.
```

It is not finding my ESSID, even if I set it up correctly in the network manager. So, everything seems to work fine, but I have no connection. I tried using DHCP, then a static address... only cable connection is working. I followed this [guide]("https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688") step by step on the livecd, as I think my wireless adapter is the atheros, as I can see it from lspci. Any idea why I can't connect?
Thanks!

---

### Post by cyberdork33 on 2008-02-15
> **Luc484 said:**
> I followed this [guide]("https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688") step by step on the livecd, as I think my wireless adapter is the atheros, as I can see it from lspci. Any idea why I can't connect?Unfortunately I don't think this is going to work for you on the livecd, because you need to reboot to reload the kernel and the new drivers (blocking the old driver).

---

### Post by Luc484 on 2008-02-15
Oh... The guide reported those commands to load the drivers without having to reboot, and they gave me no errors. Strange that the networks are successfully recognized... Well... Then I will install the OS hoping to have more luck... Thanks!

---

### Post by cyberdork33 on 2008-02-15
> **Luc484 said:**
> Oh... The guide reported those commands to load the drivers without having to reboot, and they gave me no errors. Strange that the networks are successfully recognized... Well... Then I will install the OS hoping to have more luck... Thanks!It is likely network-manager that is having the problem. You could try restarting dbus:
```
sudo /etc/init.d/dbus restart
```

---

### Post by Luc484 on 2008-02-15
No, it seems it is not working yet. If I set the IP manually, I see it with ifconfig, with DHCP I see nothing. Maybe the drivers are not working...

---

