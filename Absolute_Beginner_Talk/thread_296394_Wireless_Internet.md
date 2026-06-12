---
title: "Wireless Internet"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by jasrog on 2006-11-09
Ok I have internet connection working from wireless router on my desktop but cannot connect wireless on laptop what do I do to connect on my laptop?

---

### Post by dbott67 on 2006-11-09
Please post the output of the following commands:
```
ifconfig -a
```
```
cat /etc/network/interfaces
```
```
sudo lshw -C network
```

-Dave

---

### Post by jasrog on 2006-11-09
i did the first two commands on my notebook but cannot paste info because I cannot get online with laptop but my laptop is right next to me with that info on it...

---

### Post by dbott67 on 2006-11-09
Do you have a USB thumb drive (or floppy drive)?  You can always redirect the output to a file and then copy it to the thumbrive:
```
ifconfig -a > ifconfig.txt
```
```
cat /etc/network/interfaces > interfaces.txt
```
```
sudo lshw -C network > lshw.txt
```

Bring it over to windows and then paste it here.  The files should be in your home directory.

---

### Post by jasrog on 2006-11-09
no thumb drive. One other thing I noticed was that when I click on network it is enabled to a wired interface not wireless. Wireless option does not even appear....

---

### Post by dbott67 on 2006-11-09
Wireless networking in linux can be daunting at times, as many vendors do not release drivers to the community.  having said that, it is possible to get it working (most of the time it requires using something called 'ndsiwrapper').

Before you get started, we need to know the make & model of your wireless card (Broadcom, Intel, etc.).

The **lshw -C network** command (stands for 'List hardware for the Network Class'). **lspci** will also provide some insight (stands for 'List all PCI devices').

From my laptop:
```
dbott@dapper:~$ lspci

0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7145
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:03:01.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0000:03:01.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
0000:03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0000:03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
[COLOR="Red"]0000:0b:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)
[/COLOR]
```
```
dbott@dapper:~$ sudo lshw -C network
Password:
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:ce:31:88:6f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       [COLOR="Red"]configuration: broadcast=yes driver=ndiswrapper driverversion=1.25 firmware=Broadcom,11/02/2005, 4.10.40.0 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:dfcfc000-dfcfffff irq:169[/COLOR]
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:0c:ad:05
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=0.97 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:df9fe000-df9fffff irq:217

```

You'll notice that I'm running a Broadcom 4311 wireless card and am using ndsiwrapper to get it working.

-Dave

---

### Post by matma on 2006-11-10
> **dbott67 said:**
> Do you have a USB thumb drive (or floppy drive)?  You can always redirect the output to a file and then copy it to the thumbrive:
```
ifconfig -a > ifconfig.txt
```
```
cat /etc/network/interfaces > interfaces.txt
```
```
sudo lshw -C network > lshw.txt
```

Bring it over to windows and then paste it here.  The files should be in your home directory.

Hi,

I have an internet connection from wireless router: it works on Windows XP, but it doesn't as soon I reboot my laptop (TOSHIBA Satellite Pro M15-S405) with Ubuntu 6.06

Here there are the info about my system:

ifconfig -a > ifconfig.txt

```

eth0      Link encap:Ethernet  HWaddr 00:00:39:91:99:AF  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:04:23:48:0B:75  
          inet6 addr: fe80::204:23ff:fe48:b75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:3914 dropped:3914 overruns:0 frame:0
          TX packets:165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:44172 (43.1 KiB)
          Interrupt:11 Base address:0x2000 Memory:fcefe000-fcefefff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2340 (2.2 KiB)  TX bytes:2340 (2.2 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```


cat /etc/network/interfaces > interfaces.txt


```


auto lo
iface lo inet loopback



iface eth0 inet dhcp



iface eth1 inet dhcp
wireless-essid Home
wireless-key ####-####-##




auto eth1

auto eth0

```


sudo lshw -C network > lshw.txt


```
  
*-network:0
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 83
       serial: 00:00:39:91:99:af
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.14-k4-NAPI duplex=half firmware=N/A link=no multicast=yes port=MII speed=10MB/s
       resources: iomemory:fceff000-fcefffff ioport:cf40-cf7f irq:11
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: a
       bus info: pci@02:0a.0
       logical name: eth1
       version: 04
       serial: 00:04:23:48:0b:75
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=1.1.4 firmware=712.0.3:3:00000001 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:fcefe000-fcefefff irq:11

```

Hope somebody can give some help, thanks.

---

### Post by dbott67 on 2006-11-10
What is the output of:
```
iwlist eth1 scanning
```

You should see your AP (Home).  If so, try this:

```
sudo ifdown eth1
```
```
sudo ifup eth1
```
```
sudo dhclient eth1
```

---

### Post by matma on 2006-11-10
> **dbott67 said:**
> What is the output of:
```
iwlist eth1 scanning
```

You should see your AP (Home).  If so, try this:

```
sudo ifdown eth1
```
```
sudo ifup eth1
```
```
sudo dhclient eth1
```

here there are the outputs of the commands:

sudo iwlist eth1 scanning

```

eth1      Scan completed :
          Cell 01 - Address: 00:12:BF:26:AC:73
                    ESSID:"Home"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:2
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11
                    Quality:84  Signal level:0  Noise level:0
                    Extra: Last beacon: 216ms ago

```

It seems that the laptop can see the router but cannot connect.


sudo ifdown eth1:

```

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:04:23:48:0b:75
Sending on   LPF/eth1/00:04:23:48:0b:75
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.2.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; Device or resource busy.

```


sudo ifup eth1:

```


Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:04:23:48:0b:75
Sending on   LPF/eth1/00:04:23:48:0b:75
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```


sudo dhclient eth1:

```


Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:04:23:48:0b:75
Sending on   LPF/eth1/00:04:23:48:0b:75
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
Trying recorded lease 192.168.2.2
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

```

thank you for your help,

---

### Post by dbott67 on 2006-11-10
It could be WEP encryption that's causing the problem.  Normally, I recommend disabling encryption to eliminate WEP as the problem.  Disable it on the router & remove the 'wireless-key' line from /etc/network/interfaces and try to connect.  If you are able to connect, then we can focus on WEP.

**_Re-enabling WEP:_**

If you are able to connect without WEP, try turning it back on in the router and use 128-bit encryption with a simple 13-character password (such as 'wepencryption')

In your **/etc/network/interfaces** try changing the line to:

```
wireless-key s:wepencryption
```
The preceding 's:' idicates that the key is in plain ASCII text & should be 13 characters long (assuming you're using 128-bit).

'sudo ifdown eth1', 'sudo ifup eth1', 'sudo dhclient eth1' and see what happens.

If it works, then change the WEP key to something more difficult and repeat the above steps.


-Dave

---

### Post by matma on 2006-11-10
> **dbott67 said:**
> It could be WEP encryption that's causing the problem.  Normally, I recommend disabling encryption to eliminate WEP as the problem.  Disable it on the router & remove the 'wireless-key' line from /etc/network/interfaces and try to connect.  If you are able to connect, then we can focus on WEP.

**_Re-enabling WEP:_**

If you are able to connect without WEP, try turning it back on in the router and use 128-bit encryption with a simple 13-character password (such as 'wepencryption')

In your **/etc/network/interfaces** try changing the line to:

```
wireless-key s:wepencryption
```
The preceding 's:' idicates that the key is in plain ASCII text & should be 13 characters long (assuming you're using 128-bit).

'sudo ifdown eth1', 'sudo ifup eth1', 'sudo dhclient eth1' and see what happens.

If it works, then change the WEP key to something more difficult and repeat the above steps.


-Dave


yes! Great! It works!! Following your suggestions I've tried a couple of ASCII text passwords and everythings works fine! 

Here are the outputs (which seem look good):

sudo ifdown eth1
```

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:04:23:48:0b:75
Sending on   LPF/eth1/00:04:23:48:0b:75
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.2.1 port 67
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; Device or resource busy.

```

Is this error important?


sudo ifup eth1
```

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:04:23:48:0b:75
Sending on   LPF/eth1/00:04:23:48:0b:75
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.2.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.4 -- renewal in 984297873 seconds.

```


sudo dhclient eth1
```

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:04:23:48:0b:75
Sending on   LPF/eth1/00:04:23:48:0b:75
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.4 -- renewal in 984297849 seconds.

```

......and now it works. So was the Hex password I used the problem?

Now that I'm connected I'm very happy; however for the wifi connection I would like to use the WPA encryption. How can I set it on Ubuntu? Do I have to install some extra packages? 

Thank you very very much,

---

### Post by dbott67 on 2006-11-10
I wouldn't worry about the error (it was when you were disabling the interface, not enabling).

As for whether or not it was the Hex password, I don't know, but it's seems that it was related to WEP, so it could have been the problem.

I've never used WPA.  There are a couple of how-tos:
[http://www.jeremychapman.info/cms/WPA-on-Ubuntu-Dapper-6.06-LTS](http://www.jeremychapman.info/cms/WPA-on-Ubuntu-Dapper-6.06-LTS)
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

The first one looks simple, the 2nd one looks daunting.  If you're up for another challenge, go for it.  If you live in a fairly residential neighbourhood that's not going to be susceptible to some war-driving kid, I wouldn't lose much sleep over it.  Just add a few more layers to your security:

1. Change WEP key regularly
2. Use MAC filtering on router
3. Change router password regularly
4. Reduce DHCP leases to the total number of devices on your network (i.e. don't have a range of 100 IPs if you only have 4 computers --- lower the reange from .100-.103)

-Dave

---

### Post by matma on 2006-11-11
> **dbott67 said:**
> I wouldn't worry about the error (it was when you were disabling the interface, not enabling).

As for whether or not it was the Hex password, I don't know, but it's seems that it was related to WEP, so it could have been the problem.

I've never used WPA.  There are a couple of how-tos:
[http://www.jeremychapman.info/cms/WPA-on-Ubuntu-Dapper-6.06-LTS](http://www.jeremychapman.info/cms/WPA-on-Ubuntu-Dapper-6.06-LTS)
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

The first one looks simple, the 2nd one looks daunting.  If you're up for another challenge, go for it.  If you live in a fairly residential neighbourhood that's not going to be susceptible to some war-driving kid, I wouldn't lose much sleep over it.  Just add a few more layers to your security:

1. Change WEP key regularly
2. Use MAC filtering on router
3. Change router password regularly
4. Reduce DHCP leases to the total number of devices on your network (i.e. don't have a range of 100 IPs if you only have 4 computers --- lower the reange from .100-.103)

-Dave


Hi, ok so I think Im going to stick with WEP encryption for a while to
see whether I have some problems and then maybe I will think about WPA.

Actually I still have two small issues about wifi connection:
1) Even if my laptop is the only computer connected to the router,
it gets ALWAYS the same IP (192.168.2.4). Any idea why? Yesterday
when I eventually was able to connect my laptop, it got 192.168.2.4 as
there were other 2 pc connected at the same time. Can this be linked
with this issue?

2) Although my wifi works fine, the 'Network Manager' doesn't show me the
option for a Wireless network. It shows me only the wired network.

Can you shed light on these problems?

cheers,

---

### Post by dbott67 on 2006-11-11
For #1 DHCP-assigned addresses are "leased" to computers for a period of time.  The IP address is basically 'reserved for your computer until the lease expires.  Depending on the DHCP server settings, this can be anywhere around 8 days or so.  As long as you re-connect within the lease period, you'll probably get the same IP.

-Dave

---

