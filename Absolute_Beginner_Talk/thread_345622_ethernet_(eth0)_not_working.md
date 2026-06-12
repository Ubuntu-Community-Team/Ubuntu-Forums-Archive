---
title: "ethernet (eth0) not working"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by unknown_zohaib on 2007-01-24
Hi guys,

yes im a newbie to linux... sorta ... ill accept all the bashing anways... i searched and read all over the place and well my ethernet card doesnt seem to be working when i installed ubuntu. i have a realtek 8139 card .. one of those models on my laptop... well im actually totally lost... not sure where to begin.... im not getting any ip assigned and cant browse any websites.. i think maybe the drivers might be outdated but note sure how to update them... any helps would be appreciated!

-zee

---

### Post by unknown_zohaib on 2007-01-24
ok i did a lspci and here are the results


Ethernet controller: REaltek semiconductor Co., Ltf. RTL-8139/8139C-8132C+ (rev 10)


ifconfig

eth0     Link encap: Ethernet   HWaddr 00:C0:9F:3E:B4:BE
           inet6 addr: fe80:2c0:9fff:fe3e:b4be/64 Scope:Link
           UP BROADCAST RUNNING MULTICASE MTU:1500 Metric: 1
           RX packets:9 errors:0 dropped:0 overruns:0 frame:0
           TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:3443 (3.3 KiB) TX bytes:4824 (4.7 KiB)
          interrupt:209 Base address:0xe800

lo        Link encap: Local Loopback
           inet addr: 127.0.0.1   Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:16436 Metric: 1
           RX packets:2 errors:0 dropped:0 overruns:0 frame:0
           TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:100 (100.0 b) TX bytes:100 (100.0 b)

---

### Post by unknown_zohaib on 2007-01-24
lsmod | grep 8139too results in

8139too      29056   0
mii           9612   1  8139too

---

### Post by xael on 2007-01-24
zee,

If your network card isn't detected by Ubuntu, it's not configured out of the box, but you can help the system by supplying it with the information it can't get. 

How?. Easy. Click "Applications", "Accesories", "Terminal" and when it opens, write:

```
sudo pppoeconf
```

Now, enter your information and hit "Yes" everytime. Go back to Firefox and try to surf to any website. Enjoy.

---

### Post by unknown_zohaib on 2007-01-24
thanks for your response!

i tried that and i got a error saynig access concentrator of your provider did not respond... etc...

i got some more information 

---------------------------------------------


dmesg | grep eth -------

eth0: RealTek RTL8139 chip tyoe 'RTL-8101;
eth0: link down
ADDRCONF (NETDEV_UP): eth0: link is not ready
eth0: linkup, 100MBps, full-duplex, lpa 0x45E1
ADDRCONF (NETDEV_CHANGE): eth0: link becomes ready
eth0: no IPv6 routers present
eth0: link down
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
eth0: link up, 100Mbps, full-duplex, lpa 0X45E1
eth0: no IPv6 routers present

cat /etc/network/interfaces -------

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth0

cat /etc/resolv.conf -------

search Type address

lsmod | grep e100  -------
e100 	38020  0
mii	6912   2  e100, 8139too


lsmod | grep 8139too -------

8139too 	29056 	0
mii		6912 	2 e100,8139too

lsmod | grep 8139 -------

8139too 	29056 	0
mii		6912 	2 e100,8139too

---

### Post by unknown_zohaib on 2007-01-24
ok i figured out my problem... there is somthing wrong with my switch./... i went to on my campus and hooked my laptop up to the net there and everything worked smooth... my switch is aopen aow-605m ... i tried to find an firemware upgrade for the switch and couldn't locate anything on their website... i guess if anyone here has a solution then please let me know thanks.

---

