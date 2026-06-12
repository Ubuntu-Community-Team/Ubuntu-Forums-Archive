---
title: "Xubuntu: connect to wireless network"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by henrikfromnorway on 2006-04-18
Hello!

I have xubuntu, and installed ndiswrapper and my wireless usb-card.

but then, when i wanted to connect to my network, it wont.

when i type iwlist wlan0 scan , my network (T3) comes up. But i can't connect!

help me!!!!!!!

---

### Post by macdo on 2006-04-18
Can you give us a bit more info, please. 

What do you get when you type ```
ifconfig wlan0
```or ```
sudo ifup wlan0
```
Did you configure your wireless connection: ```
sudo iwconfig wlan0 channel [x] essid [essid] mode Managed 
```([x] and [essid] are taken from the result of iwlist wlan0 scan)
Did you start the connection? ```
sudo ifup wlan0
```

---

### Post by neonlug on 2006-04-18
I am having this issue with Ubuntu.  I belive the same answer applies for both distro's.  So I hoping you could help me also.

Here is the outout of the commands you asked for.

ifconfig wlan0
```
[FONT="Courier New"]
phillipw@Dell5150:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:90:4B:6B:F7:76
          inet6 addr: fe80::290:4bff:fe6b:f776/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:faffc000-faffdfff
[/FONT]

```

iwlist wlan0 scan
```
[FONT="Courier New"]
phillipw@Dell5150:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:0F:B5:3C:46:D7
                    ESSID:"REALINK"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-52 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
[/FONT]

```

sudo iwconfig wlan0 channel 6 essid REALINK mode
```
[FONT="Courier New"]
phillipw@Dell5150:~$ sudo iwconfig wlan0 channel 6 essid REALINK mode Managed
Password:
[/FONT]

```


sudo ifup wlan0
```
[FONT="Courier New"]
phillipw@Dell5150:~$ sudo ifup wlan0
ifup: interface wlan0 already configured
[/FONT]

```

sudo ifdown wlan0
```
[FONT="Courier New"]
phillipw@Dell5150:~$ sudo ifdown wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 9669
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:90:4b:6b:f7:76
Sending on   LPF/wlan0/00:90:4b:6b:f7:76
Sending on   Socket/fallback
[/FONT]

```

sudo ifup wlan0
```
[FONT="Courier New"]
phillipw@Dell5150:~$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 1
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:90:4b:6b:f7:76
Sending on   LPF/wlan0/00:90:4b:6b:f7:76
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
[/FONT]

```

My system sees the hardware, however I can never connect to a wireless network.  I have included the details of the network I am trying to connect to now, however it is the same regardless of the network.

Below is my /etc/network/interface file.
```
[FONT="Courier New"]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp
iface wlan0 inet dhcp
wireless-essid REALINK
wireless-key ***********
wireless-channel 6
wireless_mode Managed


auto wlan0

auto eth0
[/FONT]

```

---

### Post by macdo on 2006-04-18
HAve a look at your router settings. I know that my router allows filtering by MAC address - that's the wireless card hardware address - which would explain why you can't connect...
I'd also suggest (if practical) that you test the connection without encryption.

---

### Post by henrikfromnorway on 2006-04-18
i don't have ANY encryption, and the mac-adress is cleared. 

```

hc@westbeach:~$ sudo ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:90:96:66:49:72
               inet6 addr: fe80::290:96ff:fe66:4972/64 Scope:Link
               UP BROADCAST RUNNING  MTU:1500  Metric:1
               RX packets:0 errors:0 dropped:0 overruns:0 frame:0
               TX packets:1229 errors:0 dropped:0 overruns:0 carrier:0
               collisions:0 txqueuelen:1000
               RX bytes:0 (0.0 b)  TX bytes:406764 (397.2 KiB)


hc@westbeach:~$ sudo ifup wlan0
ifup: interface wlan0 already configured


```


btw, the router is working properly.

i'm running a server behind it, so.

---

### Post by macdo on 2006-04-18
Okay; start by typing these commands:
```
sudo ifdown wlan0
sudo iwconfig wlan0 channel [x] essid [essid] mode Managed
sudo ifup wlan0
```

If you get a line that says something like ```
ignoring unknown interface wlan0=wlan0
``` then follow these additional steps…
```
sudo mousepad /etc/network/run/ifstate
```
Add a line that says “wlan0=wlan0&#8243; (without the quotes), and save.
```
sudo mousepad /etc/network/interfaces
```
Add a line that says “iface wlan0 inet dhcp” and save.
```
sudo ifdown wlan0
sudo ifup wlan0
```

---

### Post by henrikfromnorway on 2006-04-19
i'll try later, heading off to work in a minute. :)

thanks, mate.

---

### Post by henrikfromnorway on 2006-04-24
okey, i fixed it.

it was this REALLY stupid problem.

first, the card was connected through an USB-hub.

and, since i used static local IP, by a mistake, i disabled the mac adress. :S


works fine now.

---

