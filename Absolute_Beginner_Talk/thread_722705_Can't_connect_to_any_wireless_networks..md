---
title: "Can't connect to any wireless networks."
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by drunkmatador on 2008-03-12
I'm running the newest version of Ubuntu, downloaded onto DVD ISO and then installed onto laptop computer. Everything worked right away other than the Broadcom BCM94311 wlan adapter. Drivers were downloaded as well as installed and since then networks have been showing up as usual.

However, I can't connect to the networks. At first I thought this was because my laptop's MAC was no longer allowed on the server machine (shared wifi at my apartment complex). Earlier today I called them and my MAC is actually still allowed, so it should be working. This was a surprise to me.

When running an iwlist scan, the two networks that usually show up, do. And have signal strength around -65 and around the same for noise. Kind of a lot of noise from all the access points and cordless phones around here (none of which are mine). Anyways the networks show up, I just can't connect to them for some reason.

When running dhclient on the machine it reports of having no dhcp offers recieved, and no working leases in persistent database. I don't know much about this program and whether that is relative or not, but maybe you could tell me.

And when i run sudo route -n it says that 169.254.0.0 is a destination connection using this card (eth0), but that's a fake IP, right? Could it be part of the problem?

If theres any advice you've got let me know. I'll be checking this all day.

---

### Post by InfinityCircuit on 2008-03-12
A couple of questions:

1. What kind of encryption is being used by the network?

2. What is the output of "sudo iwconfig" and "sudo ifconfig"?

---

### Post by drunkmatador on 2008-03-12
There's no encryption over the network, other than that it allows my MAC address to connect to it, whereas most it wouldn't. I know that this MAC is registered with the server since I just talked with them on the phone earlier and double checked - it should be working.

Here is the output for some of the commands I think might be helpful.




zac@zac-laptop:~$ sudo iwconfig
[sudo] password for zac:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"pearl-4"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.422 GHz  Access Point: 00:00:00:00:00:00   
          Bit Rate=11 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=65/100  Signal level=-62 dBm  Noise level=-66 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0





zac@zac-laptop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:154727 errors:0 dropped:4737 overruns:0 frame:0
          TX packets:790 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:211281284 (201.4 MB)  TX bytes:82928 (80.9 KB)
          Interrupt:10 Base address:0x8000 

eth1:avah Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet addr:169.254.8.57  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6052 (5.9 KB)  TX bytes:6052 (5.9 KB)





zac@zac-laptop:~$ sudo route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth1



zac@zac-laptop:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 5859
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:00:00:00:00:00
Sending on   LPF/eth1/00:00:00:00:00:00
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

