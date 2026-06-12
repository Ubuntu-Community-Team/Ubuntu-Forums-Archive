---
title: "Help Connecting to Network and Getting Internet"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by Crypto77 on 2007-11-16
Ok basically I am running Gutsy with and have a Zonet ZEW1602 wireless card, with drivers I installed using this tutorial [http://ubuntuforums.org/showthread.php?t=403139&highlight=zonet+ZEW1602]("http://ubuntuforums.org/showthread.php?t=403139&highlight=zonet+ZEW1602")
I then went to System/Administration/Network for the "Wireless Connection" tab went to properties and entered my ESSID, Password Type, and Network Password, and under "Connection Settings" set the Configuration to "automatic configuration (DHCP)."

I then clicked ok and then clicked the check box next to my wireless connection.  I then go to Firefox type something in the search bar and get a "server not found" which is what happens no matter what URL I try to visit.  So, I was kind of stumped and ran an "iwconfig" to check things out.  Here's the output:

> lo           no wireless extensions

eth0      no wireless extensions

wlan0    IEEE   802.11g  ESSID: off/any
             Mode:Managed  Channel:0  Access Point: Not associated
             Bit Rate:1 Mb/s   Sensitivity=200 dBm
             RTS  thr=2346 B   Fragment thr=2346  B
             Power Management: off
             Link Quality:0  Signal Level:0  Noise Level:0
             Rx  invalid nwid:0  Rx  invalid crypt:0  Rx invalid frag:0
             Tx excessive retries:0  Invalid misc:0  Missed beacon:0

However when I run a "iwlist scan"  I get:

> lo         interface doesn't support scanning

eth0     interfaced doesn't support scanning

wlan0  scan completed :
            Cell 01 - Address 00:11:24:0B:9C:6B
                           ESSID: [COLOR="Red"]"the ESSID of my router - its correct"[/COLOR]
                           Protocal:IEEE  802.11g
                           Mode: Managed
                           Frequency:2.1412 GHz (Channel 1)
                           Quality 32/100  Signal Level: -75 dBm  Noise level dBm
                           Encryption key: on
                           Bit Rates: 1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                                            9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                                            48 Mb/s; 54 Mb/s
                          Extra:bcn_int=100
                          Extra:atim=0

Here are the details of my Wireless connection in Vista, where I am connected to the network and have internet (what I am typing on write now)

> Connection-specific DNS Suffix: dc.dc.cox.net
Description: Marvell Libertas 802.11b/g Wireless LAN Client Adapter
Physical Address: 08-10-74-09-F3-16
DHCP Enabled: Yes
IPv4 IP Address: 10.0.1.5
IPv4 Subnet Mask: 255.255.255.0
Lease Obtained: Friday, November 16, 2007 10:54:53 PM
Lease Expires: Saturday, November 17, 2007 2:54:51 AM
IPv4 Default Gateway: 10.0.1.1
IPv4 DHCP Server: 10.0.1.1
IPv4 DNS Server: 10.0.1.1
IPv4 WINS Server: 
NetBIOS over Tcpip Enabled: Yes
Link-local IPv6 Address: fe80::3943:8ddb:c906:3840%9
IPv6 Default Gateway: 
IPv6 DNS Server: 

So it appears that it sees my network (in Ubuntu)- but why isn't it connecting - or is it just not letting me have internet?  Any help?  Should I be doing something with the DNS in System/Administration/network (and if so - what?).  I am lost as to why it is not working.  

P.S.  If this should be in "Wireless and Networking" let me know and I will delete this thread a make a different one over there.

---

### Post by Tatterdemalian on 2007-11-16
Try doing an ifconfig -a

Check and see if you see something like this:
> 
wlan0     Link encap:Ethernet  HWaddr 00:1A:73:81:1D:C0  
          inet6 addr: fe80::21a:73ff:fe81:1dc0/64 Scope:Link
          UP BROADCAST RUNNING MTU:1500  Metric:1
          RX packets:25168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20377 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33884669 (32.3 MB)  TX bytes:1998895 (1.9 MB)
          Interrupt:9 Memory:b8000000-b8004000 

wlan0:ava Link encap:Ethernet  HWaddr 00:1A:73:81:1D:C0  
          inet addr:169.254.6.184  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:9 Memory:b8000000-b8004000 


If you do, then you're having the same problem I am... good luck getting help for it, #avahi on Freenode IRC just tells me to throw away Ubuntu and install a "real" distro that uses ip for everything.

---

### Post by Crypto77 on 2007-11-16
My output from "iconfig -a" is thus
> eth0      Link encap:Ethernet  HWaddr 00:1B:FC:25:66: DF  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 08:10:74:09:F3:16  
          inet addr:10.0.1.5  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::a10:74ff:fe09:f316/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4640 (4.5 KB)  TX bytes:4773 (4.6 KB)
          Interrupt:21 Memory:feae0000-feaf0000 
I really don't know what that tells me though.

---

### Post by Tatterdemalian on 2007-11-17
It lists all your network interfaces, including ones that are "down" (disabled), Try running ifconfig again, without the -a, and see if the wlan0 interface still shows up. If it doesn't, 
```
ifconfig wlan0 up
```
should solve the problem.

If it's still listed, the problem is elsewhere. Since everything else is working, there's only two things I know of to try:

1. Run 
```
nm-tool
```
repeatedly. This seems to "poke" network-manager and network-dispatcher, making them get around to automatically fixing whatever is wrong.
2. Run 
```
sudo dhclient
```
This will jettison your old DHCP lease and try to get a new one. If you keep getting a message at the end of the negotiation saying "No DHCPOFFER received, sleeping" then the problem is that Ubuntu just can't seem to communicate with your router well enough to hook up with any of the offered DNS services. If get something telling you the session was successful (I forget the exact message), then try using the internet again, it should work then.

Unfortunately, I can't offer much more than that... I'm still a Linux n00b.

---

### Post by Crypto77 on 2007-11-17
What do you know - all it took was a reboot!  The internet is extremely slow however - I have broadand cable internet, but this thing is running at dial-up speeds - any ideas as to why that is?

---

