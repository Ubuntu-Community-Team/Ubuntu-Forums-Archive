---
title: "Ethernet Problem"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by lilbuddhist on 2007-08-04
hey there, I have looked through the forums but sadly I have not been able to find a solution to my particular problem, I am very very new to ubuntu and so I have very little experience.
My problem is basically that of after installing ubuntu, despite ethernet being connected directly, ubuntu does not seem to recognise the connection whatsoever.

I am running version 6.06 LTS 64bit. I installed from a Live CD.

In Network (under Administration) both of my ethernet adaptors appear (eth0 and eth1) but even when assigned to DHCP, activated and so forth there seems to be no internet connection available.

After reading various posts I thought I would include a couple of commands in the post, incase it is of any use: 

IFCONFIG

eth0: Link encap:Ethernet  HWaddr 00:15:f2:f4:4c:e6
inet6 addr: fe80::215:f2ff:fef4:4ce6/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU: 1500  metric: 1 
RX PACKETS: 754    errors: 0 dropped: 0 overruns: 0 frame: 0 tx packets: 0 errors :0 dropped: 973 overruns: 0 carrier: 0 collissions: 0 txqqueuelen:1000  
rx bytes: 60651 (59.2 kib) tx bytes: 0 (0.0b)   interrupt: 50  base address: 0x8000

eth1:Link encap:Ethernet  HWaddr 00:15:f2:f4:4c:e7
UP BROADCAST MULTICAST  mtu:1500  metric:1
RX packets:0  errors: 0   dropped: 0 overruns : 0  frame:0
TX packets:0  errors: 0  dropped: 0 oveeruns: 0 carrier: 0
collisions : 0 txqueuelen:1000
rx bytes:0 (0,.0b)  tx bytes: 0 (0.0b)
interrupt:223  base address: 0x20000

lo: link encap:local loopback
inet addr:127.0.0.1 mask: 255.0.0.0
inet6 addr: ::1/128 scope:host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets: 2047  errors: 0  dropped : 0 overruns: 0 frame: 0
TX packets: 2047 errors: 0 dropped: 0 overruns: 0 carrier: 0
collissions: 0 txqueuelen: 0
RX bytes: 160446 (156.6kib) TX bytes 160446 (156.6kib)

DHCLIENT3 ETH0

 listening on LPF/eth0/00:15:f2:f4:4c:e6     ///// sending on LPF/eth0/00:15:f2:f4:4c:e6      ////     Sending on    Socket/fallback         ////     dhcpdiscover on eth0 to 255.255.255.255 port 67 interval 5   //// dhcpdiscover on eth0 to 255.255.255.255 port 67 interval 9 //// dhcpdiscover on eth0 to 255.255.255.255 port 67 interval 13 /// ///dhcpdiscover on eth0 to 255.255.255.255 port 67 interval 11 /// dhcpdiscover on eth0 to 255.255.255.255 port 67 interval 11   ///   dhcpdiscover on eth0 to 255.255.255.255 port 67 interval 11       ////     dhcpdiscover on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS recieved. No working leases in persistrent database: sleeping.

I am using a Belkin 54mbps wireless router, although the connection to ubuntu is an ethernet cable (wired)

I think it is also important to note that the internet works fine in Windows (I use dual boot) and I happen to be using the wireless from the router to write this message on my laptop instead.

If there are any other commands or anything that might help anyone solve this situation I would be insanely greatful, as I was really looking forward to getting up and running with ubuntu.

The IP of my router is 192.168.2.1
There are two computers on the wired network, and my laptop that uses wireless
At one stage when fiddling with ethernet settings I did notice that mozilla seems to sit on Loading: rather than Cannot Load Page, but I am not sure if this makes any difference.

 I run an AMD dual core 4600+ x2 CPU, with an Asus Crosshair mobo. OCZ 667mhz ddr2 1024mbx2 RAM. BFG 7600GT nvidia geforce cardx2 (I run dual monitors with windows).

If there is anything else at all I can do to provide information to solve this problem I will do so. Thank you very very much if anyone is able to help me with this.

Matthew

---

### Post by jimrz on 2007-08-04
some of the current T1000 (gigabit) chipsets were not supported by the kernel for Dapper. you might try downloading the [[COLOR="Sienna"]**_"live cd"_**[/COLOR]]("http://www.ubuntu.com/getubuntu/download") for 7.04 feisty fawn since yours will likely have been added by now.

---

