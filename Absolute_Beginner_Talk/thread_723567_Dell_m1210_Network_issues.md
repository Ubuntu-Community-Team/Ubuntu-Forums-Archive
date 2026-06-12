---
title: "Dell m1210 Network issues"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by Tora on 2008-03-13
Okay,

I just installed Ubuntu on my Dell XPS M1210 in attempt to force myself to learn linux. Sadly, while the install went without a hitch I can't get either the wireless (just haven't found the driver for this) or the wired network working.

According to the information on these boards, the wired NIC should work out of the box, but I can't seem to get it working nor can I find any errors to give me any kind of an indicator as to the problem.

I must be doing something wrong, but I can't find anything actually wrong with the wired nic.

Any ideas? I got nothing... I'm more or less an expert with Windows, but new to linux, minus some real basic understanding of the command line.

---

### Post by jan quark on 2008-03-13
please post the results of these terminal commands:

```
iwconfig
sudo lshw -C network
```

---

### Post by Tora on 2008-03-13
iwconfig
```

lo no    no wireless extensions
eth0     no wireless extensions

```

sudo lshw -C network
```

  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:40:f6:9f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no module=b44 multicast=yes port=twisted pair speed=10MB/s


```

Here you go, thanks for the help.

---

### Post by jan quark on 2008-03-13
well your drivers seem to be installed
```
 configuration: driver=ipw3945 latency=0 module=ipw3945
configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no module=b44
```

can you please post the results of 

```
cat /etc/network/interfaces
sudo iwlist scan
```

---

### Post by Tora on 2008-03-13
can you please post the results of 

cat /etc/network/interfaces
```
auto lo
iface lo inet loopback


iface eth1 inet dhcp
wireless-essid Tank and Spank Inc.



iface eth0 inet dhcp

auto eth0

```
sudo iwlist scan
```
lo Interface doesn't support scanning

eth0  Interface doesn't support scanning 
```

---

### Post by Tora on 2008-03-13
Anyone know what the '/etc/network/interfaces' file is supposed look like?

I think this might be my problem but I'm not sure...

---

