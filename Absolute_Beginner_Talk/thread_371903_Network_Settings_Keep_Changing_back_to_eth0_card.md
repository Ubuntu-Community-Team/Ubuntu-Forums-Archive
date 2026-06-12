---
title: "Network Settings Keep Changing back to eth0 card"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Jamesbowden on 2007-02-27
Well I already made this post, but no one seems to be answering and to quote jkeyes0  "it's generally not advisable to bump your own threads. If you do, some people will overlook them thinking that someone else is providing answers and the problem is being resolved."

basically, I have a laptop, and i connect to a wireless modem to access the Internet. My laptop is NEVER connected through ethernet to a modem. however, ubuntu seems to think it is :S

I can connect to my WiFi network with out a problem. I set up my network setting the way i want them. and its fine. they look like this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=26148&stc=1&d=1172444363[/IMG]

However when i close network settings (web browsing still works fine) and re-open them again. it looks like this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=26149&stc=1&d=1172444363[/IMG]

as you can see my eth0 card has been reactived. Usually this is no problem, because the Wireless card still lets me connect, however some programs (namely ettercap) will defualtly use my eth0 card when it is activated, so they dont work properly.

here is the content of /etc/network/interfaces

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



```


does anyone know why this is happening?

---

### Post by annda on 2007-02-27
if you do not use your Ethernet card, you can safely comment out the eth0 lines by putting hashes (#) at the beginning.

that should get rid of the problem, which is caused by an inexplicable (to me) inability of the GUI program to read the configuration file properly.

BTW, i've had this problem too, but never paid much attention: i always thought "if it can be fixed by command line and config adjustments, fix it and forget the GUI"

---

### Post by Jamesbowden on 2007-02-27
thanks, so i comment out these lines?:

```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp
```

---

### Post by annda on 2007-02-27
yes, unless your wireless is eth1.

if you are unsure, run ifconfig from the terminal to see if your system uses eth1, ath0 or wlan0 for wireless.

you can safely comment out anything you do not use - except lo, of course.

---

### Post by Jamesbowden on 2007-02-27
Thanks very much, i was always pretty sure my Wifi card was ra0. 

ifconfig says it is to check it out

```
eth0      Link encap:Ethernet  HWaddr 00:03:0D:13:DF:BD  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84 (84.0 b)  TX bytes:84 (84.0 b)

[B]ra0       Link encap:Ethernet  HWaddr 00:11:09:21:90:43  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:fe21:9043/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:318968 errors:0 dropped:0 overruns:0 frame:0
          TX packets:456999 errors:9 dropped:9 overruns:0 carrier:0
          collisions:4437 txqueuelen:1000 
          RX bytes:438645154 (418.3 MiB)  TX bytes:24233639 (23.1 MiB)
          Interrupt:209 [/B]

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.23.1  Bcast:172.16.23.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.172.1  Bcast:172.16.172.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

wonder why its is'nt in the list.

---

### Post by Jamesbowden on 2007-02-27
Its still doing the same thing. Open Networking, Set my preferences, close it, reopen, its back the having eth0 activated.

here is the interfaces file now

```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

---

