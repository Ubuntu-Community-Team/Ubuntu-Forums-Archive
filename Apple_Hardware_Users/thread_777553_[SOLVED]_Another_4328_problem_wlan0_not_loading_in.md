---
title: "[SOLVED] Another 4328 problem? wlan0 not loading in Heron"
date: 2008-05-01
forum: Apple Hardware Users
---

### Post by a1234 on 2008-05-01
Well after  installation x3 on my MBP 2.4 C2D Penry I got a stable Heron. Getting the Wifi to work is a bear!
Question: 
After Installing the bcmwl5 via ndiswrapper can not seem to load the wlan0


a1234@a1234-laptop:~$ sudo -s
[sudo] password for a1234: 
root@a1234-laptop:~# ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4328) present
root@a1234-laptop:~# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ OK ]
root@a1234-laptop:~# 

I have done the following:

gedit /etc/modules for ndiswrapper

root@a1234-laptop:~# lsmod | grep ndiswrapper
ndiswrapper           193564  0 
usbcore               146028  7 ndiswrapper,uvcvideo,hci_usb,usbhid,ehci_hcd,uhci_hcd
root@a1234-laptop:~# 

root@a1234-laptop:~# lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth0
       version: 13
       serial: 00:1f:5b:e7:1a:b8
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=10.0.1.179 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
root@a1234-laptop:~# 

Why is wlan0 not loading ?




Any suggestion ?

---

### Post by a1234 on 2008-05-01
Looks like no solution to this problem ? Any thing else I can do please let me know. 
Again /etc/network/interfaces :
auto lo
iface lo inet loopback
auto wlan0
iface wlan0 inet dhcp

So should'nt it automatically load.

Is it the driver issue or the kernel issue.

Will appreciate some insight.

---

### Post by cyberdork33 on 2008-05-01
what is in ifconfig?

try doing:
```
sudo ndiwrapper -m
sudo ndiswrapper -ma
sudo ndiswrapper -mi
```then restart

---

### Post by a1234 on 2008-05-02
> **cyberdork33 said:**
> what is in ifconfig?

try doing:
```
sudo ndiwrapper -m
sudo ndiswrapper -ma
sudo ndiswrapper -mi
```then restart
root@a1234-laptop:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:5b:e7:1a:b8  
          inet addr:10.0.1.176  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: 2002:1813:a427:0:21f:5bff:fee7:1ab8/64 Scope:Global
          inet6 addr: fe80::21f:5bff:fee7:1ab8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10258 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7389 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13358296 (12.7 MB)  TX bytes:755879 (738.1 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1604 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1604 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81160 (79.2 KB)  TX bytes:81160 (79.2 KB)


I have to re install Heron after the ndiswrapper -xx thingy. That happen the first 3 times too. Must be compatibility problem with the latest kernel?!. Still same result not loading wlan0.
Thanks for the input.

---

### Post by cyberdork33 on 2008-05-02
> **a1234 said:**
> root@a1234-laptop:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:5b:e7:1a:b8  
          inet addr:10.0.1.176  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: 2002:1813:a427:0:21f:5bff:fee7:1ab8/64 Scope:Global
          inet6 addr: fe80::21f:5bff:fee7:1ab8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10258 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7389 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13358296 (12.7 MB)  TX bytes:755879 (738.1 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1604 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1604 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81160 (79.2 KB)  TX bytes:81160 (79.2 KB)


I have to re install Heron after the ndiswrapper -xx thingy. That happen the first 3 times too. Must be compatibility problem with the latest kernel?!. Still same result not loading wlan0.
Thanks for the input.
you have to reinstall? That doesn't make sense... why would you have to reinstall?

---

### Post by a1234 on 2008-05-02
> **cyberdork33 said:**
> you have to reinstall? That doesn't make sense... why would you have to reinstall?

Lock up @ configuring network interfaces. Multiple "failed' ndiwrapper messages.

I still appreciate your input though.

---

### Post by cyberdork33 on 2008-05-02
> **a1234 said:**
> Lock up @ configuring network interfaces. Multiple "failed' ndiwrapper messages.

I still appreciate your input though.
So remove ndiswrapper...

---

### Post by a1234 on 2008-05-02
Done. No wlan0 just eth0.

---

### Post by a1234 on 2008-05-02
Funny thing is my usb adapter will load and wlan0 will show in network. However the connection keep dropping. I guess thats another ndiswrapper quirk! Why isn't the 4328 driver loading the wlan0 module but the 2870 driver will load the wlan0?

---

### Post by a1234 on 2008-06-03
[http://ubuntuforums.org/showthread.php?t=816161](http://ubuntuforums.org/showthread.php?t=816161)

---

