---
title: "Attempting to connect to the internet."
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by Tbowboy3 on 2006-09-15
I'm trying to wirelessly connect to the internet.  I just switched from WinXP to Ubuntu and I can no longer connect to the internet (I could with XP).  I am using a Linksys 802.11g 2.4 GHz Wireless Notebook Adapter.  My router is a Linksys WRTP54G Wireless Router (Vonage VoIP as well).  I have tried hooking it directly into the router (via ethernet cable) but that produced the same result.  Firefox gives me a general could not connect error and when I try to browse for apps or other downloads through ubuntu, I cannot connect.  In my networking window, both the wlan0 and eth0 are active and the box for enable is checked.  

Thanks for any help in advance. :grin:

---

### Post by oedipuss on 2006-09-15
Hmm check if you can access the router itself.
 Maybe it's not hardware related but something wrong with the network settings. If it was a wlan problem I'd expect it to work when connected with the cable, and vice versa.

When I was trying to meddle with the network settings, I had the same problem (all ok and enabled, but no internet), and I had forgotten to enter the correct gateway address..

---

### Post by Tbowboy3 on 2006-09-15
Well, when I was using the laptop with windows xp (2 days ago) both wireless and wired connections were working fine.  You mentioned a gateway adress, where might I find that... on the router? IPconfig?

---

### Post by NetworkGuy on 2006-09-15
Tbowboy3,

From a terminal (Accessories --> Terminal) reply with the output of lspci

I think you need a driver tweak to make it work right.

---

### Post by Tbowboy3 on 2006-09-15
Could you tell me what I might be looking for in lspci because The computer that I am using ubuntu on (my windows copy was messed up) doesn't have internet connection nor a connection to the network, so short of typing it all out, what specifically am I looking for?

Edit: So I ran an ifconfig and an lspci and here are the results:

tbowboy3@Tbow-Laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:02:2E:2D:0B
          inet addr:192.168.15.11  Bcast:192.168.15.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:536 (536.0 b)  TX bytes:536 (536.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:14:F3:95
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11

tbowboy3@Tbow-Laptop:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 80)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 42)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
0000:00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
0000:00:09.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
0000:00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:00.0 VGA compatible controller: S3 Inc. VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK) (rev 01)
0000:02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

---

### Post by steve.horsley on 2006-09-16
Let's concentrate on the wired connection since that's likeky to be easier to get going. Last I read, Texas nstruments were prettty-much anti-Linux so their wireless might be a no-go.

ifcnfig shows that you have an IP address 192.168.15.11  allocated to eth0. That looks good to me. Did you configure that, or is it learned by DHCP?

Can you post the output from these?
[B]route
cat /etc/network/interfaces
cat /etc/resolv.conf[/B]

Can you ping 192.168.15.1 ?
Can you ping 82.211.81.186 ?

---

### Post by Tbowboy3 on 2006-09-16
I configured my static ip adress on here, but only to see if it helped, I can obviously change it back to DHCP easily.

tbowboy3@Tbow-Laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.15.0    *               255.255.255.0   U     0      0        0 eth0
tbowboy3@Tbow-Laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.15.11
netmask 255.255.255.0
gateway 255.255.255.0

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid linksys

tbowboy3@Tbow-Laptop:~$ cat /etc/resolve.conf
cat: /etc/resolve.conf: No such file or directory
tbowboy3@Tbow-Laptop:~$ cat /etc/resolv.conf
nameserver 192.168.15.1
tbowboy3@Tbow-Laptop:~$
 
Pings will be added in a sec.

ping 192.168.15.1: 

From 192.168.15.1 icmp_seq=[1-500] Destination Host Unreachable

ping 82.211.81.186:

connect: network is unreachable

---

### Post by Tbowboy3 on 2006-09-16
> **Tbowboy3 said:**
> I configured my static ip adress on here, but only to see if it helped, I can obviously change it back to DHCP easily.

tbowboy3@Tbow-Laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.15.0    *               255.255.255.0   U     0      0        0 eth0
tbowboy3@Tbow-Laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.15.11
netmask 255.255.255.0
gateway 255.255.255.0

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid linksys

tbowboy3@Tbow-Laptop:~$ cat /etc/resolve.conf
cat: /etc/resolve.conf: No such file or directory
tbowboy3@Tbow-Laptop:~$ cat /etc/resolv.conf
nameserver 192.168.15.1
tbowboy3@Tbow-Laptop:~$
 
Pings will be added in a sec.

ping 192.168.15.1: 

From 192.168.15.1 icmp_seq=[1-500] Destination Host Unreachable

ping 82.211.81.186:

connect: network is unreachable
dsa

---

### Post by steve.horsley on 2006-09-17
If you are going to configure statically, you need to also configure a default route to the local router and also the IP address of a DNS server for doing name lookups.

Do you know the IP address of the local router? Unless your Ethernet interface is broken, it's not my first guess of 192.168.15.1. Do you also know the IP address of a DNS server to use? If you don't know the answers to these two questions, you could either use DHCP in which case the router should tell you, or get a command prompt on XP and type in the command:
**ipconfig /all**
and post the result.
You can add the default route to Linux with the command:
**sudo route add default gw 1.2.3.4**
replacing 1.2.3.4 with your router's IP address.
You can add the DNS server's IP address to /etc/resolv.conf (no e after the v).

If you want to try DHCP again, reconfigure the interface using the GUI and then try the command:
**sudo dhclient eth0**
and post the output, then 
**ifconfig**
and post the output.

---

### Post by Tbowboy3 on 2006-09-17
Yes, my router's IP is 192.168.15.1 as is my desktop computer.  So, if I make my box's 192.168.15.1 won't I get an error that I am using the same IP on twice or something like that?  (I had that problem and occasionally the DHCP would set the laptop's IP to the same as the desktop's static IP.)

Results:
> 
**tbowboy3@Tbow-Laptop:~$ sudo route add default gw 192.168.15.1**
SIOCADDRT: File exists
**tbowboy3@Tbow-Laptop:~$ sudo dhclient eth0**
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:08:02:2e:2d:0b
Sending on   LPF/eth0/00:08:02:2e:2d:0b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
**tbowboy3@Tbow-Laptop:~$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:08:02:2E:2D:0B
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3976 (3.8 KiB)  TX bytes:3976 (3.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:14:F3:95
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11


---

### Post by kh4nh on 2006-09-17
> 
tbowboy3@Tbow-Laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.15.11
netmask 255.255.255.0
gateway 255.255.255.0


Shouldn't your gateway be 192.168.15.1 or 192.168.15.254

---

### Post by buffy^ on 2006-09-17
no
it should be 192.168.15.1

---

### Post by Tbowboy3 on 2006-09-17
Should I change it back to static 192.168.15.1 or DCHP?

Results:

> **tbowboy3@Tbow-Laptop:~$ sudo route add default gw 192.168.15.1**
SIOCADDRT: File exists
**tbowboy3@Tbow-Laptop:~$ sudo dhclient eth0**
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:08:02:2e:2d:0b
Sending on   LPF/eth0/00:08:02:2e:2d:0b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
**tbowboy3@Tbow-Laptop:~$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:08:02:2E:2D:0B
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3976 (3.8 KiB)  TX bytes:3976 (3.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:14:F3:95
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11


---

### Post by steve.horsley on 2006-09-17
Well, I can see something wrong but I don't know what to do about it. dhclient should have transmitted several packets while trying to contact a DHCP server. But after all that, ifconfig still says 0 bytes / packets sent. I wonder if you have driver problems there (I assume the cable is plugged in).

Maybe you would be better off trying to get the wireless going after all, but I don't know much about wireless. Perhaps start a new thread. Someone who does know about wireless might want to see the output from **iwconfig** and **iwscan list**.

---

### Post by firefoxu on 2006-09-17
I had a similar issue. I tried as suggested on these threads and it worked for me.

[http://ubuntuforums.org/showthread.php?t=151725&highlight=network+dead](http://ubuntuforums.org/showthread.php?t=151725&highlight=network+dead)

[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

---

### Post by Tbowboy3 on 2006-09-17
New update, I tried the method in the updated thread but got nothing from wlan0 or eth0.  

I can however (while I am wired into the router) see my shared files on the desktop.

---

### Post by Tbowboy3 on 2006-09-18
bump

---

