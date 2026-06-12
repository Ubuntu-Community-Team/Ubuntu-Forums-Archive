---
title: "Internet works, network doesnt, please help"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by rabosajr on 2006-10-08
I'm a new ubuntu user and installed kubuntu in one of my pc. Somehow during my last update I screwed things up.
I cant find other computers in my wired network nor can i install a network printer but the internet works.
This is my /etc/network/interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
address 192.168.1.3
netmask 255.255.255.224
gateway 192.168.1.1


iface eth1 inet static
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.1

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth1

but running ifconfig config in the terminal returns

eth1      Link encap:Ethernet  HWaddr 00:04:75:E7:1C:F1
          inet addr:169.254.28.94  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::204:75ff:fee7:1cf1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1393 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1077 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1020081 (996.1 KiB)  TX bytes:171262 (167.2 KiB)
          Interrupt:193 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:57 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3480 (3.3 KiB)  TX bytes:3480 (3.3 KiB)

ping from a pc running windows xp shows that this pc (ip address 192.168.1.3) is connected

I have tried to set ip address to static in the networks settings but I dont know why the ip address I put is somehow changed.

Any help here will be much appreciated. Thanks

---

### Post by iamnafets on 2006-10-11
First of all, thank you to everyone manning this forum.  I actually read through some of the guides listed in the stickies and was able to blacklist a crappy driver and install ndiswrapper on one of my computers.  Being new to linux, and having hardware a major obstacle to switching, I can now say that I'm dual booting but running almost exclusively Ubuntu and enjoying it tremendously.  Thank you to everyone!

But...I'm having a similar problem.

I have a desktop wirelessly connected to a router (this is the one that doesn't work) and a laptop connected to the same router.  With obvious hardware differences, both are running Ubuntu 6.06.  The laptop can ping everyone on the network and the internet, it works great.  The desktop can access the internet (I'm on it now) and ping the router, it cannot see anything else.  I'm absolutely puzzled.  Any help/bump?

---

### Post by Phill Kenoyer on 2007-11-07
bump, Same here.  I can't ping the local network but I can access the internet just fine.  Seems like a firewall issue.  Does Ubuntu come with a firewall enabled?  I have too much work to do...back to the Mac for now.

---

### Post by swoll1980 on 2007-11-07
Yes by default all ports are closed. Try installing the samba server see if that opens them up for you

---

