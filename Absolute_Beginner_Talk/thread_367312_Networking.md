---
title: "Networking"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by Cave Dweller on 2007-02-22
Hello again, everyone.

I'm sorry for posting this question, I'm sure that I've seen the answer already, either on the fora, or somewhere in the support documents.  But I'm having a bad brain day, today, so hopefully someone can point me in the right direction.

I have an ADSL router connecting with DHCP over Eth0.  When I boot, there seems to be about a 50% chance that the connection is made automatically.  The rest of the time, I need to manually open networking and dis-able, re-enable the connection.  It's not a critical problem, but it's a bit irritating.  Is there a setting somewhere that I can tweak?

Thank you all for your time and patience.

---

### Post by Stephen Howard on 2007-02-22
very odd, does the /var/log/mesages offer any clues about what is going wrong?

---

### Post by Cave Dweller on 2007-02-22
Hi Steve.  Thanks for answering,

I'm sorry but I wouldn't even know what to look for in /var/log/messages.  These lines seem to be about my network card, but I don't really know.

Feb 22 15:57:06 localhost kernel: [17179594.168000] Linux Tulip driver version 1.1.13 (December 15, 2004)
Feb 22 15:57:06 localhost kernel: [17179594.168000] **** SET: Misaligned resource pointer: eab008a2 Type 07 Len 0
Feb 22 15:57:06 localhost kernel: [17179594.168000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
Feb 22 15:57:06 localhost kernel: [17179594.168000] PCI: setting IRQ 11 as level-triggered
Feb 22 15:57:06 localhost kernel: [17179594.168000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Feb 22 15:57:06 localhost kernel: [17179594.200000] tulip0:  EEPROM default media type Autosense.
Feb 22 15:57:06 localhost kernel: [17179594.200000] tulip0:  Index #0 - Media 10baseT (#0) described by a 21142 Serial PHY (2) block.
Feb 22 15:57:06 localhost kernel: [17179594.200000] tulip0:  Index #1 - Media 10baseT-FDX (#4) described by a 21142 Serial PHY (2) block.
Feb 22 15:57:06 localhost kernel: [17179594.200000] tulip0:  Index #2 - Media 100baseTx (#3) described by a 21143 SYM PHY (4) block.
Feb 22 15:57:06 localhost kernel: [17179594.200000] tulip0:  Index #3 - Media 100baseTx-FDX (#5) described by a 21143 SYM PHY (4) block.
Feb 22 15:57:06 localhost kernel: [17179594.204000] eth0: Digital DS21142/DS21143 Tulip rev 48 at 0001ec00, 00:00:F8:07:4B:74, IRQ 11.

I had a quick look in /var/log/syslog.  I have a few entries along these lines

Feb 22 15:57:45 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Feb 22 15:57:50 localhost kernel: [17179653.552000] eth0: no IPv6 routers present
Feb 22 15:57:54 localhost dhclient: No DHCPOFFERS received.
Feb 22 15:57:54 localhost dhclient: No working leases in persistent database - sleeping.

And I think this is me in networking dis-connecting / re-connecting

Feb 22 15:58:50 localhost dhclient: Listening on LPF/eth0/00:00:f8:07:4b:74
Feb 22 15:58:50 localhost dhclient: Sending on   LPF/eth0/00:00:f8:07:4b:74
Feb 22 15:58:50 localhost dhclient: Sending on   Socket/fallback
Feb 22 15:58:50 localhost dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Feb 22 15:58:50 localhost dhclient: send_packet: Network is unreachable
Feb 22 15:58:50 localhost dhclient: send_packet: please consult README file regarding broadcast address.
Feb 22 15:58:51 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.3
Feb 22 15:58:51 localhost dhclient: Copyright 2004-2005 Internet Systems Consortium.
Feb 22 15:58:51 localhost dhclient: All rights reserved.
Feb 22 15:58:51 localhost dhclient: For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
Feb 22 15:58:51 localhost dhclient: 
Feb 22 15:58:52 localhost dhclient: Listening on LPF/eth0/00:00:f8:07:4b:74
Feb 22 15:58:52 localhost dhclient: Sending on   LPF/eth0/00:00:f8:07:4b:74
Feb 22 15:58:52 localhost dhclient: Sending on   Socket/fallback
Feb 22 15:58:56 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Feb 22 15:58:56 localhost dhclient: DHCPOFFER from 192.168.1.1
Feb 22 15:58:56 localhost dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Feb 22 15:58:56 localhost dhclient: DHCPACK from 192.168.1.1
Feb 22 15:58:56 localhost dhclient: bound to 192.168.1.100 -- renewal in 1528 seconds.
Feb 22 15:59:02 localhost kernel: [17179724.964000] eth0: no IPv6 routers present
Feb 22 15:59:14 localhost gconfd (root-4983): GConf server is not in use, shutting down.
Feb 22 15:59:14 localhost gconfd (root-4983): Exiting
Feb 22 16:17:01 localhost /USR/SBIN/CRON[5706]: (root) CMD (   run-parts --report /etc/cron.hourly)
Feb 22 16:24:24 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Feb 22 16:24:24 localhost dhclient: DHCPACK from 192.168.1.1
Feb 22 16:24:24 localhost dhclient: bound to 192.168.1.100 -- renewal in 1497 seconds.

I don't know if that's helpful.

---

### Post by Stephen Howard on 2007-02-22
The syslog is revealing - I think that dhclient probes the network using ip 255.255.255.255 only after it doesn't receive a lease.  

As a test, when it boot without networking, what happens if you type:

[INDENT][FONT="Fixedsys"]ifconfig eth0 up[/FONT][/INDENT]

Can you provide the output of the following:
[LIST=1]
[*]ifconfig

[*]cat /etc/network/interfaces

[*]ps aux | grep dhc
[/LIST]

[INDENT](and if the above grep lists a command containing "-lf", provide a cat of the file referenced immediately after - it should have a path /var/run/dhclient.*)[/INDENT]

PS:  sorry if the above isn't too clear - trifle drunk on champagne!

---

### Post by Cave Dweller on 2007-02-23
Isn't it always the way, I want the computer to boot without connecting and the computer decides that today is a good day to surf the net.  

:~$ ifconfig eth0 up
SIOCSIFFLAGS: Permission denied

:~$ sudo ifconfig eth0 up
Password:

I couldn't tell if this did anything, it didn't enable my connection.

:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:F8:07:4B:74
          inet6 addr: fe80::200:f8ff:fe07:4b74/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:0 overruns:0 frame:0
          TX packets:0 errors:11 dropped:0 overruns:0 carrier:33
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface dsl-provider inet ppp
provider dsl-provider

I'm sorry, I wrote the last one down incorrectly, and so this is the result after I have established the internet connection.  Do you need the results of this one when the connection is not working?

:~$ ps aux | grep dhc
dhcp      5327  0.0  0.1   2332   792 ?        Ss   17:10   0:00 /sbin/dhclient3 -pf /var/run/dhclient.eth0.pid eth0
nargun    6557  0.0  0.1   2892   816 pts/0    S+   17:51   0:00 grep dhc

Thanks for helping me with this, I appreciate it.  I'm a bad champagne drinker, I'm afraid, I prefer the $5 bottle of local sparkling to the moet or dom.  But I've got some fairly nice home-brewed beer.  Cheers.

---

### Post by Stephen Howard on 2007-02-23
Sorry this is taking so long, but the problem isn't one I've experienced myself so I'm fishing around, and I suspect we must be in significantly different time zones!

When the network is working, what does ifconfig report?

Can you tell me your gateway IP (eg the IP of your router) and the IP of the computer?  The above ifconfig command should show that info, but I ask just in case it doesn't.

---

### Post by Stephen Howard on 2007-02-23
Oh, and what is your router's dhcp server setup?

---

### Post by Cave Dweller on 2007-02-24
Hello again.

Please, I'm just happy that you're helping me with this, no need to worry about time.  I've been living with this for months, now.  Here it's +10h 30m with daylight savings, but I have, um, irregular sleep patterns, so I'm in a different time zone to everyone.  *Laugh*  

Here's,

:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:F8:07:4B:74
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:f8ff:fe07:4b74/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:833 errors:0 dropped:0 overruns:0 frame:0
          TX packets:528 errors:2 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000
          RX bytes:1121308 (1.0 MiB)  TX bytes:40747 (39.7 KiB)
          Interrupt:11 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

I'm pretty sure the router is at 192.168.1.1

I'm not too sure about the routers DCHP setup, is this what you were after?

enable DCHP server:  yes
start IP:  192.168.1.100
end IP:  192.168.1.149
lease time: 3600 sec

---

### Post by Stephen Howard on 2007-02-24
Hi, the lease time looks really short - can you change it to 43200sec (ie 12hrs).  

I have to nip out for an hour - back soon and I'll look at the info in detail.

---

### Post by Stephen Howard on 2007-02-24
If extending the lease time doesn't work, try the following:

Edit /etc/network/interfaces and find the line that reads:
[INDENT][FONT="Fixedsys"]iface eth0 inet dhcp[/FONT][/INDENT]

Add a new line under it which reads:

[INDENT][FONT="Fixedsys"]pre-up sleep 10[/FONT][/INDENT]

With a bit of luck that will delay the network setup long enough for dhcp to be working properly.  If it does clear up the problem, experiment with lower sleep values until you find the lowest number that still fixes the problem.  If the pre-up and/or  longer-lease suggestions don't work, then I don't know how to help any further.  

Good luck.

---

### Post by Cave Dweller on 2007-03-01
Thanks Stephen, I'm giving that a bit of a try.  I think the pre-up sleep might do the trick.  I might pop back in a couple of weeks, if I'm still having problems.  Hit a bit of a busy patch.

Thanks again

---

### Post by Cave Dweller on 2007-03-12
Sorry to bother you again, Stephen.

Can I increase the preup sleep to maybe 15 or 20?  I'm not sure if I will need to, because things seem much improved.  But I'm starting to catch a bit of flak from my local greenhouse hypocrit and I'm going to have to switch off when I'm not sitting here, bah.

---

