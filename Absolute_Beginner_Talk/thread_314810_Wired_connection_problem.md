---
title: "Wired connection problem"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by SebbeJohan on 2006-12-08
Hello there,

Beginner here looking for some help!

I have this problem with my wired connection (eth0). This connection disappears often and I can't seem to be able to connect. This occurs every time I go to Uni and connect on the Wifi. As soon as I get home and plug my wired connection, nothing happens. The green light is not even blinking. I tried on the laptop on a friend and it works perfectly :( After a couple of hours, I plug in my cable, the green light blinks and Internet begin to work. However it usually doesnt last long, and the connection disappear again...
I have installed network-manager but it didn't seem to help so I uninstalled it for network selector, which doesn't help either.
Is there a conflict somewhere? I really don't know what to do.

My /etc/network/interfaces looks like that:

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


My ifconfig gives the following (I'm on the Wifi at Uni)

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:50:DB:2E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:6 

eth1      Link encap:Ethernet  HWaddr 00:0E:35:29:60:68  
          inet addr:130.236.66.50  Bcast:130.236.67.255  Mask:255.255.254.0
          inet6 addr: fe80::20e:35ff:fe29:6068/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:74655 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8469 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15063194 (14.3 MiB)  TX bytes:1096025 (1.0 MiB)
          Interrupt:10 Base address:0x6000 Memory:d0208000-d0208fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2443 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2443 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:157198 (153.5 KiB)  TX bytes:157198 (153.5 KiB)


Can someone help me with this? What other information is needed? My connection is a 100mb with no modem (or at leat I can't see it, I plug in my cable directly into a small box in the wall)

Thanks in advance

---

