---
title: "Network Manager shows wireless card as wired?"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by flatfish on 2007-01-13
Very new at this, I searched for this problem but couldn't find anything, sorry if it's been asked before.  I'm trying to set up a Gigabyte GN-WP01GS card to connect to an existing access point.  I am using Ubuntu 6.10 and have installed Network-Manager and Network-Manager-Gnome using Synaptic Package manager.   Left-clicking on Network Manager shows the following:  

Wired Network (Davicom Semiconductor, Inc. 21x-4x DEC Tulip Compatible 10/100 Ethernet)
Wired Network (Ralink RT2561/RT61 802.11g PCI)

The Ethernet connection is selected and appears to be working, as I am connected right now.   

In the terminal: I get the following:


network-manager
bash: network-manager: command not found


iwconfig
lo        no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          
eth0      no wireless extensions.

sit0      no wireless extensions.


ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:53:80:BD:39  
          inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:53ff:fe80:bd39/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2472 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1496 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1188047 (1.1 MiB)  TX bytes:215703 (210.6 KiB)
          Interrupt:15 Base address:0x1400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:E6:3B:22:29  
          UP RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:7488 (7.3 KiB)
          Base address:0x8000 

wmaster0  Link encap:UNSPEC  HWaddr 00-16-E6-3B-22-29-00-80-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x8000 


Any ideas?

---

### Post by teaker1s on 2007-01-14
it's possibly because your /etc/iftab file will need the correct "eth" line commented out by
#
 to become wlan, but if it works I wouldn't worry

---

### Post by Bealer on 2007-01-29
I've got exactly the same card, and problem. I'm also running Edgy.

It just seems to identify my wireless card as a wired card. I tried the above mention, but it made no difference.

---

### Post by nzruss on 2007-02-11
having the same problem here.

---

### Post by DraconPern on 2007-11-27
Still having the same problem with 7.10 with an airvast card w/ wlan-ng

---

