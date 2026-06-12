---
title: "Wired Networking - Not Connecting"
date: 2010-09-02
forum: Apple Hardware Users
---

### Post by downindm on 2010-09-02
I just installed Ubuntu 10.04 on an old G4 Mac desktop.  Install went great with no issues.  

However, connecting it to the wired network seems to be next to impossible.  I also have OS X 10.4 on the same machine (different drive) and copied all the network setting so I know they are correct.  It's not picking up anything from the DHCP server, and I've tried entering everything manually.  No matter what I try, it seems as if it just doesn't want to connect.  The Mac connects fine.

ifconfig looks good (everything UP) on "eth0" but there is no IP address showing although I have one entered.

Also, I can't even seem to ping the IP address as it says network is unreachable.  

The fact that it works on OS X but not Ubuntu (on the same machine) is driving me nuts... I've put many Macs and PC's on our network so I know all the settings are correct - the only thing new to me is that "Routes" button.  Do I need to put anything in there???

---

### Post by linuxopjemac on 2010-09-03
If you have an Apple router I would set it up to have 13 characters passwords (to make it work with the world outside the Apple bubble box).

---

### Post by downindm on 2010-09-03
Nope, it's not an Apple router... This is actually on a federal government network, and I believe all our switches and routers are Cisco equipment.

---

### Post by anubhavrocks on 2010-09-03
Can you post the output of:
sudo dhclient eth0

---

### Post by downindm on 2010-09-03
I managed to get it working.  I pulled the network card out of an old PC and put it in the Mac and configured it and the network came right up.  I'm guessing that the drivers for the onboard ethernet (which works fine on the Mac) aren't included on the install CD.  Also note, it had nothing to do with the DHCP server as I was configuring both manually.

---

### Post by anubhavrocks on 2010-09-03
I suggested that command, as i just wanted to check if you manual config had some issue.

Had there been no driver, you would not see eth0 at all.

Maybe you could have tried ethtool.

---

### Post by downindm on 2010-09-08
Ok, I only have things half working... I have a link now, and am using DHCP (had our network guys give me an IP).  So, it shows the network is now connected, and I have a valid IP address and everything - and can ping myself.  However it seems as if all my traffic is one way.  Packets go out, but nothing comes back.  Trying to ping any other host on the network results in a "Destination Host Unreachable".  I am able to ping things if I boot into OS X.

---

### Post by downindm on 2010-09-08
Here's a little more info...

/etc/network/interfaces:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

/etc/resolv.conf:

nameserver 130.46.250.105
nameserver 130.46.250.106

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:08:a1:03:ee:48  
          inet addr:130.46.162.91  Bcast:130.46.163.255  Mask:255.255.254.0
          inet6 addr: fe80::208:a1ff:fe03:ee48/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:406 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:26161 (26.1 KB)
          Interrupt:53 Base address:0x400 

eth1      Link encap:Ethernet  HWaddr 00:03:93:ac:21:0c  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14809 (14.8 KB)  TX bytes:14809 (14.8 KB)

netstat -rn:

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
130.46.162.0    0.0.0.0         255.255.254.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         130.46.162.1    0.0.0.0         UG        0 0          0 eth0

---

### Post by downindm on 2010-09-09
Ok, I'm about to throw this thing out a window... Someone, anyone???

I've reinstalled about 10 times.  System is a PowerMac3,6.  I gave up on the other network card (Davicom 9102) - having physically removed it - and have gone back to trying to get the built in wired network port working (as it should supposedly do right out of the box from what I've read).  It works with no issue under OS X 10.4 and gets a DHCP address assigned with no issues, so that seems to tell me the hardware and connection are fine.

Here is what ifconfig under OS X looks like:
```
lo0: flags=8049<UP,LOOPBACK,RUNNING,MULTICAST> mtu 16384
    inet6 ::1 prefixlen 128 
    inet6 fe80::1%lo0 prefixlen 64 scopeid 0x1 
    inet 127.0.0.1 netmask 0xff000000 
gif0: flags=8010<POINTOPOINT,MULTICAST> mtu 1280
stf0: flags=0<> mtu 1280
en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
    inet 130.46.162.61 netmask 0xfffffe00 broadcast 130.46.163.255
    ether 00:03:93:ac:21:0c 
    media: autoselect (100baseTX <full-duplex>) status: active
    supported media: none autoselect 10baseT/UTP <half-duplex> 10baseT/UTP <full-duplex> 10baseT/UTP <full-duplex,hw-loopback> 100baseTX <half-duplex> 100baseTX <full-duplex> 100baseTX <full-duplex,hw-loopback> 1000baseT <full-duplex> 1000baseT <full-duplex,hw-loopback> 1000baseT <full-duplex,flow-control> 1000baseT <full-duplex,flow-control,hw-loopback>
fw0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 2030
    lladdr 00:03:93:ff:fe:ac:21:0c 
    media: autoselect <full-duplex> status: inactive
    supported media: autoselect <full-duplex>

```Now, under Lucid:
```
eth0      Link encap:Ethernet  HWaddr 00:03:93:ac:21:0c  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0x2c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 B)  TX bytes:300 (300.0 B)

```Here is what "lshw -C Network" gives me:
```
  *-network               
       description: Ethernet interface
       product: UniNorth 2 GMAC (Sun GEM)
       vendor: Apple Computer Inc.
       physical id: f
       bus info: pci@0002:20:0f.0
       logical name: eth0
       version: 00
       serial: 00:03:93:ac:21:0c
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sungem driverversion=0.98 duplex=half latency=16 link=no maxlatency=64 mingnt=64 multicast=yes port=MII speed=10MB/s
       resources: irq:41 memory:f5200000-f53fffff memory:f5100000-f51fffff(prefetchable)

```Just to check that the driver is loaded I did a "lsmod | grep sun" which gives me:
```
sungem                 32704  0 
sungem_phy             12365  1 sungem

```Running a "dhclient eth0" gives me:
```
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:03:93:ac:21:0c
Sending on   LPF/eth0/00:03:93:ac:21:0c
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```Here's the output of "dmesg | grep eth0":
```
[    6.840737] eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:03:93:ac:21:0c
[    6.840746] eth0: Found BCM5421 PHY
```All of this is on a fresh install of Lucid.  When DHCP failed to fetch an address, I used Network Manager to enter things manually with the following info:

IP: 130.46.162.61
Mask: 255.255.254.0
Gateway: 130.46.162.1
DNS Servers: 130.46.250.105, 130.46.250.106
Search Domain: dt.navy.mil, nswccd.navy.mil

I know these are the correct settings as this is also what OS X picks up when the DHCP server assigns it an address.  I'm at my wits end, any help would be GREATLY appreciated!

---

### Post by linuxopjemac on 2010-09-09
[https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsApple](https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsApple)

What I read is that Lucid supports less hardware nowadays. I would not be surprised if Ubuntu Karmic Koala still works. I think it has to do with the sungem module. Maybe there is a bug in there. You could also try Debian. Im am pretty sure that with Debian Lenny you will have no problems.

---

### Post by downindm on 2010-09-09
> **linuxopjemac said:**
> [https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsApple](https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsApple)

What I read is that Lucid supports less hardware nowadays. I would not be surprised if Ubuntu Karmic Koala still works. I think it has to do with the sungem module. Maybe there is a bug in there. You could also try Debian. Im am pretty sure that with Debian Lenny you will have no problems.

Yep, looks like the support for the built-in ethernet port (or the Davicom 9102 card I tried) just isn't there in Lucid.  I scrounged around and found an Intel PCI card and it's up and running with no issues.  Next up, to see if my Adaptec SCSI card is gonna work and if I'm gonna be able to mount an old SGI XFS volume.

Thanks!

---

