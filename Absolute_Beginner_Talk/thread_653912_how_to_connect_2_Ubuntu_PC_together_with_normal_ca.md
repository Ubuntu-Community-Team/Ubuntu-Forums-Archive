---
title: "how to connect 2 Ubuntu PC together with normal cat5 cable"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-12-30
see my PC specs below in signature
====================

**2nd laptop is a friends**, its a **PPC G3 white translucent iBook apple mac / 128MB / 800MHz**
(Darwin Kernel Ver 6.1, Fri Sep 6 PDT 2002)
(iBook revision = 2.2)
(ROM 4.5.4f1

it was in Japanese so thats all i could dig out of it
anyway it was running or more i should say was creeping on OS 10.2

the iBook has no internal wifi card so the guy went out and bought a 

**Air Plus DWL-G122 D-Link**

but that only works with OS 10.3 and higher

so we got some OS10.3 disc and it was impossible to install

so i download ubuntu 6.06LTS PPC version, the installation took hours and hours

well now its finidhed, so how to make it connect to the internet?

i get a wifi signal from my window, we have no access to a router physically

**how to connect 2 Ubuntu PC together with normal cat5 cable**

i am connected to the internet now via wifi, can i hook his laptop to mine with a cat5 cable
so he can access the internet

i think this works in windows.

thanks

=========================

**can someone please give easy step by step instructions**, the aim is to get the ibook laptop to have internet access through my laptop, is this possible? (coz ubuntu 6.06 is not recognizing the D-Link USB wifi adapter and needs to be updated I guess)

---

### Post by MozartlovesUbun2 on 2007-12-30
[http://cdimage.ubuntu.com/ports/releases/gutsy/release/](http://cdimage.ubuntu.com/ports/releases/gutsy/release/)

just found this :-)

---

### Post by HermanAB on 2007-12-30
I sometimes do this with my laptop, to hook up another machine.

Assuming that the internet connection is on wlan0 and the LAN wire to the other PC is on eth0, here is a simple NAT script for sharing an internet connection:

# Enable IP forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward

# Create a NAT firewall
iptables -I FORWARD -i wlan0 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -I FORWARD -i eth0 -o wlan0 -j ACCEPT
iptables -t nat -I POSTROUTING -o wlan0 -j MASQUERADE


Remember to use a cross-over LAN cable.

Cheers,

Herman

---

