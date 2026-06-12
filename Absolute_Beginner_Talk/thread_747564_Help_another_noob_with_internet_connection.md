---
title: "Help another noob with internet connection"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by id1337x on 2008-04-06
I got a new HP pavillion a633f PC: 
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01297099&lc=en&cc=ca&lang=en&product=3645666&dlc=en]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01297099&lc=en&cc=ca&lang=en&product=3645666&dlc=en")

Anyways I decided to install Ubuntu 7.10 and well there is no internet. When I ping [www.ubuntu.com](www.ubuntu.com) it says "unknown host" and when I ping 82.211.81.158 it says "host unreachable." Anyways, it recognizes the device properly. It says RTL 8111/8168 Express Ethernet Gigabit Controller. 

So when I check for driver by typing lshw -C network it says **illegal vendor id** so I think that that means I need to have drivers or something??

---

### Post by Michael.Godawski on 2008-04-06
Can you please post the whole output of 

```
sudo lshw -C network
iwconfig
```

---

### Post by pseudo-random on 2008-04-06
I'll need more info if I'm to offer help.
How are you connecting to the net? Is it direct or via a home NAT router?
Are you using a static IP address or dynamic?
Before you start pinging can you run ```
ifconfig
``` and ```
route
```
to check you've got a path to the internet first.

---

### Post by id1337x on 2008-04-06
Ok here is more information:

iwconfig

```
lo        no wireless extensions.
  
eth0      no wireless extensions.
 
```

lshw -C network

```

*-generic
  description: Ethernet interface
  product: Illegal Vendor ID
  vendor: Illegal Vendor ID
  physical id: 0
  businfo: pci@0000:0Z:00.0
  logical name: eth0
  version: ff
  serial: 00:le:8c:35:9c:76
  width: 32 bits
  capabilities: bus_master vga_palette cap_list ethernet physical
  configuration: broadcast=yes driver=8169 driverversion=2.2LK latency=255 maxlatency=255 minint=255 module=r8169 multicast=yes


```

---

### Post by id1337x on 2008-04-06
route


```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0
```

---

### Post by pseudo-random on 2008-04-06
ifconfig not iwconfig (thats for wireless adaptors.)

---

### Post by Crafty Kisses on 2008-04-06
Try this:
```
ifconfig
```
You may also want to see if you're receiving any packets from a website:
```
ping website name.com
```

---

### Post by id1337x on 2008-04-06
Michael.Godawski asked me to put out iwconfig even though I'm not using wireless. I don't really know why. Anyways I just got ifconfig here it is:

```
eth0         Link encap: Ethernet HWaddr 00:1E:8C:35:89:9C:7B
             UP BROADCAST RUNNING MULTICAST MTU:1500 Metric: 1
             RX packets: 0 errors: 0 dropped: 4294967289 overruns: 0 frame: 0
             TX packets: 0 errors: 0 dropped: 0 overruns: 0 carrier: 0
             collisions: 0 txqueuelen: 1000
             RX bytes: 0 (0.0 b)  TX bytes: 0 (0.0 b)
             Interrupt: 17 Base Address: 0x2000

lo           Link encap: Local Loopback
             inet addr: 127.0.0.1 Mask: 255.0.0.0
             UP LOOPBACK RUNNING MTU: 16436 Metric: 1
             RX packets: 0 errors: 0 dropped: 0 overruns: 0 frame: 0
             TX packets: 0 errors: 0 dropped: 0 overruns: 0 carrier: 0
             collisions: 0 txqueuelen: 0
             RX bytes: 0 (0.0 b) TX bytes 0 (0.0 b)
```

---

