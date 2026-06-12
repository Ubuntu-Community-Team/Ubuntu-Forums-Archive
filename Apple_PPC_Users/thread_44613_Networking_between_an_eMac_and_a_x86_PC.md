---
title: "Networking between an eMac and a x86 PC"
date: 2005-06-27
forum: Apple PPC Users
---

### Post by Ptero-4 on 2005-06-27
Hi. I just received the Ubuntu hoary x86 CD's that I ordered from shipit some time ago and decided to try the LiveCD in my sister's HP Pavilion PC. I took a rj45 network cable and connected it to my eMac and the x86 PC. Since that x86 PC have a winmodem I decided to use the eMac to connect to my dialup ISP and relay Web access to the x86 PC through a small LAN between my eMac and the x86 PC, but being a n00b in networking I obviously am having big problems trying to get the PC to see my eMac and I wanted to know. Can you give me or point me to a step-by-step guide on:
1) Setting a network with static IP/DNS under Mac OS X 10.3.9 and having the computer be able to connect to the internet through it's modem and use the ethernet to share the internet connection.

2) Setting a network via DHCP under Ubuntu and connect to the internet through the ethernet link.

Thanks.

---

### Post by az on 2005-06-27
Regardless of the architecture, they are both linux computer connected through an ethernet cable.

On the computer connected to the net, you need to do NAT (masquerading) to share the internet connection.  You also need to masquerade dns.  You also asked for a DHCP setup?

Install dnsmasq.  It acts as a DNS masquerader as well as a dhcp server.  You need to edit the names of your devices in /etc/dnsmasq but that is straightforward.

You want to go from ppp0 to eth0.

You can do NAT with ipmasq.  Install ipmasq and you will need to install the DHCP server rule (usr/share/doc/ipmasq/examples/basics) into etc/ipmasq/rules.

It sounds a lot more complicated than it is.

---

### Post by gruepig on 2005-06-27
[QUOTE=Ptero-4]Hi. I just received the Ubuntu hoary x86 CD's that I ordered from shipit some time ago and decided to try the LiveCD in my sister's HP Pavilion PC. I took a rj45 network cable and connected it to my eMac and the x86 PC. Since that x86 PC have a winmodem I decided to use the eMac to connect to my dialup ISP and relay Web access to the x86 PC through a small LAN between my eMac and the x86 PC, but being a n00b in networking I obviously am having big problems trying to get the PC to see my eMac and I wanted to know. Can you give me or point me to a step-by-step guide on:
1) Setting a network with static IP/DNS under Mac OS X 10.3.9 and having the computer be able to connect to the internet through it's modem and use the ethernet to share the internet connection.

2) Setting a network via DHCP under Ubuntu and connect to the internet through the ethernet link.

Thanks.[/QUOTE]
 If you have the two computers directly connected via an Ethernet cable, you'll need a crossover cable.  You can tell whether you have a regular (straight-through) or crossover cable by looking at both RJ45 ends.  If the colors of the 8 wires are in the same order on both ends, you have a straight-through cable.  You'll need a crossover cable or a switch/hub before you can connect the two computers.

In OS X, I suspect if you enable "Internet Sharing" (via the Sharing System Preference), NAT and DHCP will be enabled.

On the Linux box: DHCP is probably the default, but if it isn't, modify /etc/network/interfaces.  Run 'ifdown eth0; ifup eth0' (assuming eth0 is your Ethernet device) and then take a look at the output of 'ifconfig' and try pinging the Mac and hosts outside your network (by both IP and hostname). 

Good luck.

---

### Post by Ptero-4 on 2005-06-27
[QUOTE=gruepig]If you have the two computers directly connected via an Ethernet cable, you'll need a crossover cable.  You can tell whether you have a regular (straight-through) or crossover cable by looking at both RJ45 ends.  If the colors of the 8 wires are in the same order on both ends, you have a straight-through cable.  You'll need a crossover cable or a switch/hub before you can connect the two computers.

In OS X, I suspect if you enable "Internet Sharing" (via the Sharing System Preference), NAT and DHCP will be enabled.

On the Linux box: DHCP is probably the default, but if it isn't, modify /etc/network/interfaces.  Run 'ifdown eth0; ifup eth0' (assuming eth0 is your Ethernet device) and then take a look at the output of 'ifconfig' and try pinging the Mac and hosts outside your network (by both IP and hostname). 

Good luck.[/QUOTE]
 The colors of the 8 wires are not in the same order on both ends, but aren't in the opposite order either. They're just in different order.

---

### Post by gruepig on 2005-06-28
[QUOTE=Ptero-4]The colors of the 8 wires are not in the same order on both ends, but aren't in the opposite order either. They're just in different order.[/QUOTE]

Yes, that's correct. 10/100 Mbit connections use only two pairs of wires (1,2,3,6).  Most likely you have a functioning crossover cable.  If you're curious about the exact wiring, see [http://www.cisco.com/warp/public/701/14-g_small.gif](http://www.cisco.com/warp/public/701/14-g_small.gif).

---

