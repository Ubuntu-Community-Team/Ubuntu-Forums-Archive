---
title: "[SOLVED] Help needed: Hardy, Wireless, Powerbook"
date: 2008-06-23
forum: Apple Hardware Users
---

### Post by LeSid on 2008-06-23
Hi all

My goal is to have a minimal version of ubuntu running on my power book. I
used the ppc mini install disk and use fluxbox while trying to avoid gnome
or kde-dependencies for performance reasons. So I'm working mostly from the command line. 

In order to get the wlan up, I installed bcm43xx-fwcutter and rebooted. The wlan didn-t work. 

I tried the following:

```
sudo aptitude install bcm43xx-fwcutter
```

Rebooted

```
lspci |grep -i net
0001:10:12.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0002:24:0f.0 Ethernet controller: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM) (rev 80)
```

 ```
sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 12
       bus info: pci@0001:10:12.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=16 module=ssb
  *-network
       description: Ethernet interface
       product: UniNorth 2 GMAC (Sun GEM)
       vendor: Apple Computer Inc.
       physical id: f
       bus info: pci@0002:24:0f.0
       logical name: eth0
       version: 80
       serial: 00:11:24:84:ae:00
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sungem driverversion=0.98 duplex=full ip=192.168.1.137 latency=16 link=yes maxlatency=64 mingnt=64 module=sungem multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:24:97:56:f1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

```
sudo modprobe bcm43xx
```

 ```
sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such file or directory
```

What is it I'm missing?

---

### Post by owlgorithm on 2008-06-27
Use ```
sudo aptitude install b43-fwcutter
``` instead :-)

---

### Post by LeSid on 2008-06-27
Thanks!

```
sudo ifconfig wlan0 up
``` 
brought it up and
```
sudo iwconfig
```
didn't produce an error. 

```
sudo iwlist wlan0 scanning
```
showed the available wlans and
this tutorial helped me set up the connection:
[http://wiki.ubuntuusers.de/WLAN/wpa_supplicant]("http://wiki.ubuntuusers.de/WLAN/wpa_supplicant")

Wireless connection is now established.

---

