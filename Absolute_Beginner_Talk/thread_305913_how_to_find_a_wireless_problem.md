---
title: "how to find a wireless problem"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by justrust on 2006-11-24
ok, i've read a lot of forums, but i'm just stuck.  i think its the basics that i dont get.

i used the firmware cutter on my appleairport2 file and installed it. and reloaded the module like this guy said: [http://ubuntuforums.org/showthread.php?t=303393&highlight=airport](http://ubuntuforums.org/showthread.php?t=303393&highlight=airport) - now my network shows up (using kwifimanager), and further more i have seemed to be connected in some sense or another once in the past (connection properties claimed that packets were recieved at one point, though not since my most recent reboot).

although i'm not exactly sure what its supposed to say,

```
ifconfig eth0
```

tells me:

```
eth0      Link encap:Ethernet  HWaddr 00:14:51:78:C3:5F
          UP BROADCAST MULTICAST  MTU:1500  METRIC:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:18004 (17.5 KiB)  TX bytes: 738 (738.0 b)
          interrupt:52 Base address:0xc000
```

and

```
sudo dhclient
```

leads to

```
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:14:41:78:c3:5f
Sending on   LPF/eth0/00:14:41:78:c3:5f
Listening on LPF/eth0/00:11:24:d2:33:98
Sending on   LPF/eth0/00:11:24:d2:33:98
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

so do these outputs give any indication of where my networking is failing?  because ping certainly doesnt do anything, but thats about as much as i know how to investigate.

thanks guys
rusty

---

### Post by Bachstelze on 2006-11-24
Are you pretty sure eth0 is your wireless interface ? Please paste the output of

```
sudo iwconfig
```

---

### Post by justrust on 2006-11-24
yeah i am, but here's the output:
```
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate: 1 Mb/s   Tx-Power=17dBm
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0  Missed beacon0

sit0      no wireless extensions.
```

r

---

