---
title: "Wifi edimax EW-7318USG no tira"
date: 2009-04-23
forum: Catalan Team
---

### Post by indiosincracia on 2009-04-23
Hola, tinc un wifi edimax EW-7318USG 
he instalat rutilt, sembla que necessito el driver rt73-cvs-daily.tar.gz per fer-lo rutllar, però no el trobo.
c3pox@indiu:~$ iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.467 GHz  Access Point: 00:18:39:89:A4:FB
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=11/70  Signal level=-84 dBm  Noise level=-95 dBm
          Rx invalid nwid:11085  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.
c3pox@indiu:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:13:f7:3d:15:8d
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:f7ff:fe3d:158d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12702 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12671 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9358730 (8.9 MB)  TX bytes:1247883 (1.1 MB)

eth0      Link encap:Ethernet  HWaddr 00:1d:60:f8:7e:ae
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5600 (5.4 KB)  TX bytes:5600 (5.4 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-13-F7-3D-15-8D-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44595 errors:0 dropped:0 overruns:0 frame:4568
          TX packets:13313 errors:10 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:12244898 (11.6 MB)  TX bytes:1554946 (1.4 MB)
          Interrupt:16
c3pox@indiu:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.2
Release:        8.04
Codename:       hardy

ara estic conectat amb una pci smcwpcit-g
merci

---

### Post by indiosincracia on 2009-04-24
M'acabo de baixar el Jaunty Xapapote, i funciona "out of the box", oli en un llum, aquest wifi USB és compatible amb linux però encara m'abarallo amb hardy i gutsy, deu ser un bug això.

---

