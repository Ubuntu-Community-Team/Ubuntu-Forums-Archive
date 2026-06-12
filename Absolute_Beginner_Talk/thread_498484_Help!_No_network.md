---
title: "Help! No network"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Amplidude on 2007-07-11
I have a router connected to the internet. The router is connected to a server with two nic (eth0 and eth1 for the lan). eth1 is connected through a hub to PCs running XP. I can connect to the internet through the server, but can't get the PCs to see the internet or the other computers.

Thanks for replying

My setup looks like this:

dhcpd.conf
# DHCP configuration by Firestarter
ddns-update-style interim;
ignore client-updates;

subnet 192.168.0.1 netmask 255.255.255.0 {
option routers 192.168.1.1;
option subnet-mask 255.255.255.0;
option domain-name-servers Server1;
# option ip-forwarding off;
range dynamic-bootp 192.168.0.100 192.168.0.254;
default-lease-time 21600;
max-lease-time 43200;
}

etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

Do you ned any more information?

---

### Post by Alex&amp;Linux on 2007-07-13
Well, perhaps we can work it out together.
Im not sure exactly what your home network looks, so I'll draw what I thought you meant:

Home Gateway (internet) --> Eth0 Server (Linux?) Eth1 --> 10/100 Hub --> PC (XP box?)
                                                                                                     |
                                                                                                     --> PC (XP box?)

Where are the packets being dropped?
Are the boxes that cant get out getting an IP?
IF so, can you get return packets from gateway IP?
Did you make sure its not a DNS issue?
Forgive me if I'm not comprehending this, but its late, and I have to drag my *** out of bed at an ungodly hour!

Leeme know!

---

### Post by Amplidude on 2007-07-17
Hi Alex&Linux

Thanks for responding. Sorry It's taken me a while to get back to you but I trashed my internet connection and had a bit of a battle getting it back.
> Im not sure exactly what your home network looks, so I'll draw what I thought you meant:
Your drawing was close:

Internet->Router->eth0:Ububtu Server:eth1->10/100 hub->2XP boxes (although at the moment I'm only trying to connect one - hopefully the other will follow)
> Where are the packets being dropped?
I don't know where the packets are being dropped, but possibly at the firewall (firestarter). How do I check this?
> Are the boxes that cant get out getting an IP?
Yes. DHCP is working and allocates an IP to the XP box. XP reports the correct IP for the subnet, default gateway and DHCP server.
> IF so, can you get return packets from gateway IP?
Again, I'm not sure what you mean (sorry, I've only been into Linux for about a month so I'm a newbie).  If I ping I get responses every way except from the XP box to the router: specifically, I get responses from the ISP from the router, eth0 and eth1. Similarly eth0 and eth1 both see the xp box. The XP box sees eth0 and eth1 but not the router, and therefore not the ISP.
> Did you make sure its not a DNS issue?
No, I don't know how to do this. I've not loaded a DNS server (it's not necessary for my purposes). 

Let me know any other info you need. Thanks again for your response.  Ciao

PS. I posted another problem I'm having which may be related under a different thread here [http://ubuntuforums.org/showthread.php?t=503199](http://ubuntuforums.org/showthread.php?t=503199)

---

