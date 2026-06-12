---
title: "Dual NIC Problem"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by dhungda on 2006-01-14
Dear everyone...
I have a problem when setup internet connection on Breezy, I have 2 NIC and when I try to connecting to LAN I must activated 2 of them. If I deactivated one of them I couldn't connect to internet... anyone can help me? 
sorry for poor english.

---

### Post by d1337 on 2006-01-14
Can you post you /etc/network/interfaces file for us?

d1337

---

### Post by ed_d on 2006-01-14
Also, double check your Syste>Admin>network, at the bottom, you will see what it wants to use as its gateway, ent0 or ent1. Which ever is your gateway to the internet nic car, make sure that is selected. You may have to look at it again after a reboot too. I have had the same issue with a card on my pc at work, but I rarely reboot it so just have to check it once in a blue moon reboot.

---

### Post by dhungda on 2006-01-15
[QUOTE=ed_d]Also, double check your Syste>Admin>network, at the bottom, you will see what it wants to use as its gateway, ent0 or ent1. Which ever is your gateway to the internet nic car, make sure that is selected. You may have to look at it again after a reboot too. I have had the same issue with a card on my pc at work, but I rarely reboot it so just have to check it once in a blue moon reboot.[/QUOTE]

I used eth0 as a gateway... 
Is it possible just used eth0 and deactivated eth1?

---

### Post by ed_d on 2006-01-15
Sure, you can do that. Are they both on the same network? I use the ethernet card that gets me to the world as my gateway, then I have a nother nic that is a private network for running my fast t network for testing. For some odd reason it like to use the private gateway. I just disable that second nic when I am not using it.

---

### Post by dhungda on 2006-01-15
[QUOTE=ed_d]Sure, you can do that. Are they both on the same network? I use the ethernet card that gets me to the world as my gateway, then I have a nother nic that is a private network for running my fast t network for testing. For some odd reason it like to use the private gateway. I just disable that second nic when I am not using it.[/QUOTE]

Yes, both NIC in same network.
When I plug utp to eth0 - I can't connect to internet but I can reached my server in the same network.
but if plug utp cable to eth1 - I can connect to internet but  I can reached my server in tehe same network.

What should I do?

---

### Post by dhungda on 2006-01-15
[QUOTE=d1337]Can you post you /etc/network/interfaces file for us?

d1337[/QUOTE]

this is my configuration :

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet static
	address 192.168.1.99
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.1.1 

auto eth0

iface eth1 inet static
address 192.168.1.200
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1

---

### Post by dhungda on 2006-01-15
[QUOTE=dhungda]Yes, both NIC in same network.
When I plug utp to eth0 - I can't connect to internet but I can reached my server in the same network.
but if plug utp cable to eth1 - I can connect to internet but  I can reached my server in tehe same network.

What should I do?[/QUOTE]

sorry ,
if plug utp cable to eth1 - I can connect to internet but I can't reached my server in the same network.

---

### Post by mips on 2006-01-15
Post the contents of you **/etc/network/interfaces** file here.

Edit:
Sorry, must be going blind or mad, somehow I did not see the info was already posted.

---

### Post by dhungda on 2006-01-16
[QUOTE=mips]Post the contents of you **/etc/network/interfaces** file here.

Edit:
Sorry, must be going blind or mad, somehow I did not see the info was already posted.[/QUOTE]

I already post content of /etc/network/interfaces/

---

### Post by mips on 2006-01-19
[QUOTE=dhungda]
...
iface eth0 inet static
	address **[COLOR="Red"]192.168.1.99[/COLOR]**
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1

...
iface eth1 inet static
address **[COLOR="Red"]192.168.1.200[/COLOR]**
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1[/QUOTE]

You can NOT have both interface within the same network/ip subnet.

Unconfigure and disable your one NIC. You can configure that NIC for a totally seperate network though.


**_WHY?:_**
[http://www.unet.univie.ac.at/aix/aix...interfaces.htm](http://www.unet.univie.ac.at/aix/aix...interfaces.htm)
> **Implications of Multiple Network Interfaces on the Same Network**

Sometimes network managers feel the need to provide greater availability and performance by adding a second network adapter to a particular machine. For example, they may want to have two token-ring adapters attached to the same physical network. While it is possible to have more than one interface on the same network, in general this is not recommended for two reasons:

1. Having two interfaces on the same network is a violation of TCP/IP architecture.

In TCP/IP architecture, a host machine with two network adapters is defined as an IP router. Different network adapters must be attached to different physical networks. In the case of token-ring, TCP/IP addresses multiple rings bridged together as a single logical ring (as if it were a single physical ring).
2. Having two interfaces on the same network can cause broadcast storms.

Whenever an IP host sees traffic for a network whose IP address is different from its own network, it generates an Internet Control Message Protocol (ICMP) packet announcing this conflict. Since every host on the network sees the traffic that is misaddressed, every host generates ICMP packets. If the amount of misaddressed traffic is significant, the ICMP traffic can grow to the point that network performance degrades.

It is possible to avoid the broadcast storms created when multiple interfaces are connected to the same network. However, doing so is still a violation of TCP/IP architecture. The solution is to give the different interfaces different IP addresses on the same network. For example, you might have two token-ring adapters on the same network named tr0 and tr1. You must assign distinct IP addresses and names to tr0 and tr1. (TCP/IP architecture requires that each interface have a unique IP address and name; otherwise, unpredictable behavior will result.) For instance, you might give interface tr0 the IP address 10.10.10.1 and the name laurel.foo.bar.com, and interface tr1 the IP address 10.10.10.2 and the name hardy.foo.bar.com.

---

