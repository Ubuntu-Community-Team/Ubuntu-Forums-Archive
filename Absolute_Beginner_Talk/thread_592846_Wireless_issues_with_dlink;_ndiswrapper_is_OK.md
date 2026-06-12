---
title: "Wireless issues with dlink; ndiswrapper is OK"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by harpoon45 on 2007-10-26
I'm running FC: 2.6.18.1 and trying to get a DLink DWL-G122 wireless dongle to work with it. I have installed ndiswrapper-1.48 and that seems to have worked fine. I get the "Act" light flashing all the time but cannot seem to get the link to the AP.

/sbin/iwconfig wlan0 mode Managed
/sbin/iwconfig wlan0 key restricted s:sasha
/sbin/iwconfig wlan0 essid toonpoint
/sbin/iwconfig wlan0

wlan0 IEEE 802.11g ESSID:"toonpoint" Nickname:"localhost.localdomain"
Mode:Auto Frequency:2.457 GHz Access Point: Not-Associated
Bit Rate=11 Mb/s Tx-Power:20 dBm Sensitivity=-115 dBm
RTS thr=2347 B Fragment thr=2346 B
Encryption key:7361-7368-61 Security mode:restricted
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


/sbin/ifconfig wlan0

wlan0 Link encap:Ethernet HWaddr 00:13:46:E5:C9:41
inet6 addr: fe80::213:46ff:fee5:c941/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

/sbin/ifconfig wlan0 up

/sbin/dhclient

Internet Systems Consortium DHCP Client V3.0.4-RedHat
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:13:46:e5:c9:41
Sending on LPF/wlan0/00:13:46:e5:c9:41
Listening on LPF/eth0/00:08:a1:0f:e3:31
Sending on LPF/eth0/00:08:a1:0f:e3:31
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.



more ifcfg-wlan0

# Please read /usr/share/doc/initscripts-*/sysconfig.txt
# for the documentation of these parameters.
TYPE=Wireless
DEVICE=wlan0
HWADDR=00:13:46:e5:c9:41
BOOTPROTO=dhcp
NETMASK=
DHCP_HOSTNAME=
IPADDR=
DOMAIN=
ONBOOT=yes
USERCTL=no
IPV6INIT=no
PEERDNS=yes
ESSID=toonpoint
CHANNEL=1
MODE=Auto
RATE=Auto


more keys-wlan0

KEY=sasha


--------------------------------------------------
I see wlan0 in the Network configuration tool so I presume I've installed ndiswrapper properly, and didn't get any erros doing it.
When I try to activate the connection using "Network"



Error for wireless request "Set Encode" (8B2A) :
invalid argument "sasha".

Determining IP information for wlan0... failed; no link present. Check cable?


I'm not sure what the error means??? Any help????

---

### Post by spd106 on 2007-10-27
Are you able to scan for access points?
```

/sbin/iwlist wlan0 scan
```

Also check that ndiswrapper has the driver and device configured properly.

```
/usr/sbin/ndiswrapper -l
usr/sbin/ndiswrapper -v

```

---

