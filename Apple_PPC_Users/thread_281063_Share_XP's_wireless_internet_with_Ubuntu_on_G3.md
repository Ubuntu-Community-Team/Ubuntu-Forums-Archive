---
title: "Share XP's wireless internet with Ubuntu on G3"
date: 2006-10-20
forum: Apple PPC Users
---

### Post by tbar3 on 2006-10-20
](*,) ok, here's the deal: I have a wireless connection that i'm getting from my landlord's business. i have a wireless nic set up on my XP box. i have ubuntu installed on a Mac G3. i want to connect my G3 to my XP box using a crossover cable and share my internet connection. As of right now, i can't even get the 2 machines to see each other at all (still shows the Network cable is unplugged). the way it's set up is:
Wireless router -> Wireless NIC (XP) NIC -(crossover cable)-> G3 NIC

any ideas how to get the two to play nice? i've posted this in the network section to no avail... hopefully Mac user's will be more helpful??:-#

---

### Post by jaradronald on 2006-10-20
On the XP Machine you need to enable Internet Connection sharing for the wireless connection (Start-> Control Panel -> Network Connections, then RIght click on the "Wireless Network Connection", select Properties.  Go to the "Advanced" tab and under "Internet Connection Sharing" click "Allow Network Users to connect through this computers internet connection" and select your Ethernet Connect as the "Home Networking Connection:".)

Once you do this your Ethernet Connection (LAN) will be setup with a static private IP address (such as 192.168.1.x, or 172.16.1.x).  Windows will automatically select a private IP that is different than the subnet on your Wireless card.  This IP address will be the "Default Gateway" that you will need to use on your Linux box.  You will need to manually give your Linux box a static IP in the same Subnet as the IP of the Ethernet Connection on your XP Box.  For example, if the following settings were applied to your Ethernet Connection in Windows:

IP: 172.16.1.1
Subnet: 255.255.255.0

You could use the following setup on your Linux Box:

IP: 172.16.1.2
Subnet: 255.255.255.0
Default Gateway: 172.16.1.1
DNS Server: 172.16.1.1

Additionally, any 172.16.1.x address would work on the linux box.  Or you could ditch the crossover cable and hook both NICs up to a hub, and then use 172.16.1.2, 172.16.1.3, etc. for any number of client computers on your network and route their Internet traffic through 172.16.1.1 (What!?  Free router software built into Windows XP Home Edition!?  ¿Qu'est qu ce'?).

As far as cabling, the crossover cable SHOULD give you a live connection between the two (if you don't have a hub laying around).  Just try pinging back and forth once you get your IP's setup on both machines.  Once the Internet Connection Sharing is enabled in Windows your XP box will then forward all Public IP Requests and DNS Queries along to the internet and relay the information back to your Linux box.

Sounds simple enough, eh? :-k

Oh, and FYI, Windows Internet Connection Sharing doesn't act as a DHCP server, so you will have to configure the client IP's manually.

---

