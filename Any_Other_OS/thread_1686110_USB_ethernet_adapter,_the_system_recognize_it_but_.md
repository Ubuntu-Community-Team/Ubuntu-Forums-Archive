---
title: "USB ethernet adapter, the system recognize it but network is unreachable"
date: 2011-02-11
forum: Any Other OS
---

### Post by g_rus on 2011-02-11
I have a new USB ethernet adapter, sabrent

My system is Linux Mint 10 (Ubuntu 10.10)
The system recognize it, but the network is unreachable.


When I conect the USB and doing "lsusb", i get:

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0b95:772a ASIX Electronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The "ASIX..." line is my USB ehernet adapter

If i do "lspci", i get:

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

With the command "dmesg |tail -f", i get:

[  236.205874] eth1: link down
[  236.208595] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  236.225915] eth0: link down
[  236.226354] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  240.282786] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0


etho0 is my old network card that doesn't work. You can see eth1 (the newone) is down

[  236.208595] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  236.225915] eth0: link down
[  236.226354] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  240.282786] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0

With the commad "route -n" i get nothing

With ifconfig i get: 

eth1      Link encap:Ethernet  HWaddr 00:60:6e:56:6b:7b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B

I configure the netwok with ths MAC address and IP static (That is in my office)

And nsthing, doing PING to server;

connect: Network is unreachable

I activate the module mii, for this kind of card

I try put at /etc/network/interfaces, this:

allow-hotplug eth1
iface eth1 inet static
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.4

But still the same line at ping. As i can see, the system detect the card and recognize it. what can I do now? 

Thanks

---

### Post by gfwright80 on 2011-12-15
I am having a similar problem as you did when you entered this post.  Did you ever resolve the problem?  I am using a Sabrent USB Network Ethernet adapter NT-USB20, and the system detects it, attempts to connect through it, but it just doesn't get through to the net.  I attempt to install a driver i got off of the site at [PCI / USB Network Adapters, Linux Driver Support]("http://www.sabrent.com/support/knowledgebase.php?article=34").  I followed the instructions in the read-me file.  I am running Ubuntu 11.10.  

If you ever get yours working, and I know it was almost a year ago, please let me know.  

Thanks,

---

