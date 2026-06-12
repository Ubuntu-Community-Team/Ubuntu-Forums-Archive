---
title: "Totally baffled: eth0 appears fine but no connection on CentOS 4.8"
date: 2012-02-20
forum: Any Other OS
---

### Post by SuaSwe on 2012-02-20
Hi forum peeps!

Today I have been attempting to replace my ancient Ubuntu 8.04 Server install with CentOS 4.8 - had to go with an old version because anything newer and the system requirements exceed what my poor server PC has to offer. The install itself went OK-ish; I had to set boot option to 'linux nofb' to avoid getting a frozen blank screen but once I'd done that it went through OK. I have attempted the installation twice, once using my own ideas of partitioning and customised setup, and then when this failed as I am shortly to describe I tried for the automatic partitioning and default server setup, with the same result.

So, to the problem: whilst eth0 is showing as "up" in ifconfig and ethtool, and is configured with known correct settings (used on previous server install and later tested on Ubuntu LiveCD just in case), I am not getting a connection to my router, and as a result not to anything else either.

I have attached the outputs of the commands and file outputs I thought might be useful to diagnose the problem, namely: 

```

/etc/sysconfig/network
etc/sysconfig/network-scripts/ifcfg-eth0
ethtool eth0
ifconfig -a
lsmod
lspci
/etc/init.d/network restart	# produces 'irc 201' errors but restarts fine
ps -ef

```

To sum up briefly, my desired static IP config is:

IP: 192.168.0.130
Mask: 255.255.255.0
GW: 192.168.0.1

And what I have for eth0 on ifconfig, ethtool, /etc/sysconfig/network-scripts/ifcfg-eth0 and /etc/sysconfig/network are:

```

# ifconfig output
eth0      Link encap:Ethernet  HWaddr MA:CM:AC:MA:CM:AC  
          inet addr:192.168.0.130  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe92:cdcd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:120 (120.0 b)
          Interrupt:201 Base address:0xa000 

# ethtool output  
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 32
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: d
	Current message level: 0x00000007 (7)
	Link detected: yes

# /etc/sysconfig/network-scripts/ifcfg-eth0
DEVICE=eth0
BOOTPROTO=static
BROADCAST=192.168.0.255
HWADDR=00:16:36:92:CD:CD
IPADDR=192.168.0.130
NETMASK=255.255.255.0
NETWORK=192.168.0.0
ONBOOT=yes
TYPE=Ethernet

# /etc/sysconfig/network
NETWORKING=yes
HOSTNAME=myserver.com
GATEWAY=192.168.0.1

```

I tried disconnecting the ethernet cable and link detection switched to "no" then back to "yes" once reconnected, suggesting the physical link is OK - also confirmed this by connecting via eth0 with the same static settings via a Ubuntu LiveCD. 

Basically, as far as I can tell there are no issues with config, but I am still getting this:

```

user@suaserve ~]$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.130 icmp_seq=1 Desination Host Unreachable
From 192.168.0.130 icmp_seq=2 Desination Host Unreachable
From 192.168.0.130 icmp_seq=3 Desination Host Unreachable

--- 192.168.9.1 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2998ms, pipe4

```

At this point I'm assuming that one of two causes is true:

1. I am missing something glaringly obvious, maybe something that is running but shouldn't or vice versa
2. My server isn't happy with this kernel

Much Googling has not got me closer to a solution - any advice would be much appreciated!

---

### Post by SuaSwe on 2012-02-21
Bump? :)

---

### Post by boydrice on 2012-02-21
You might want to look at alternatives to CentOS 4.8 as it goes EOL on Feb 29th.  

[http://wiki.centos.org/Manuals/ReleaseNotes/CentOS4.9]("http://wiki.centos.org/Manuals/ReleaseNotes/CentOS4.9")

If you have really meager hardware specs I would look at Debian, Slackware, FreeBSD, NetBSD, or OpenBSD as options.

---

### Post by SuaSwe on 2012-02-22
Hi boydrice,

Yes, I saw that as well - not such great news for my trusty old Packard ey! Have ordered myself a new shiny nettop anyway so reckon I'll just put Ubuntu back on the laptop, if anything. :) Thanks for replying!

---

