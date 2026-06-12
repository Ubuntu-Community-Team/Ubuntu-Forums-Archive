---
title: "Wireless Networking"
date: 2005-09-30
forum: Absolute Beginner Talk
---

### Post by ZBlach on 2005-09-30
Hi,

I've just moved to a new router with my new ISP, but I've been unable to connect to it using Ubuntu (Hoary and Breezy).

I've NDISwrappered correctly, and I've matched every setting as I've setup on the router. I can see my network, and iwconfig reports a great connection, but I'm unable to browse the internet nor access the router config menu. 

What am I doing wrong?

-Z

---

### Post by tehwa on 2005-09-30
can you ping your gateway?

---

### Post by ZBlach on 2005-09-30
No.

Exact error:

"From 192.168.1.101 [me] icmp_seq=# Destination Host Unreachable"

---

### Post by tehwa on 2005-09-30
[QUOTE=ZBlach]I can see my network, and iwconfig reports a great connection, but I'm unable to browse the internet nor access the router config menu. 
What am I doing wrong?[/QUOTE]
When you say you can 'see your network', you can browse network shares between PC's?

---

### Post by ZBlach on 2005-09-30
i mean see my network like:

```

#sudo iwlist wlan0 scan

01. [Network Data]

02. [More Network Data]


```

and

```


#sudo iwconfig wlan0

[All Network Data]


```
 
I haven't got samba up yet. Haven't tried. Only installed breezy half hour ago.

---

### Post by tehwa on 2005-09-30
It strikes me as odd that (assuming that you are using DHCP) your router has given you an IP address, even though according to ping results the destination host is unreachable.

What is the exact output of an ifup wlan0? Does it definitely go through without a hitch?

---

### Post by ZBlach on 2005-09-30
it doesn't work with DHCP, even tho its setup for it. I've given myself a static IP and all. 

exact output for ifup wlan0:

"ifup: interface wlan0 already configured"

---

### Post by tehwa on 2005-09-30
[QUOTE=ZBlach]it doesn't work with DHCP, even tho its setup for it. I've given myself a static IP and all. 
exact output for ifup wlan0:
"ifup: interface wlan0 already configured"[/QUOTE]
ah, I mean sudo ifdown wlan0 && sudo ifup wlan0
You'll have to be more descriptive. When you say it doesn't work with DHCP, does that mean that there is a hardware problem/deficiency that means DHCP is impossible, or that DHCP hasn't been succesful?
It's definitely a configuration issue between your card and your router, and I'm guessing that succesfully using DHCP will resolve it. Perhaps post the contents of /etc/network/interfaces to see how it is going about connecting.

---

### Post by ZBlach on 2005-09-30
ok. DHCP works on all other computers, but not on my ubuntu. I get no success with it, same as using a static IP. but my goal is to have a static IP so that, later, when I have an FTP and other programs requiring internal access, i can forward correctly.

Contents of /etc/network/interfaces 
```

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

iface wlan0 inet static
wireless-essid Blacher
wireless-key $MY_KEY
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1

auto wlan0


```

---

### Post by tehwa on 2005-09-30
what was the result of 
```
sudo ifdown wlan0
sudo ifup wlan0
```

It appears that while your network thinks it is configured, it is not communicating with the router.

When i replied to your thread I assumed that DHCP was involved, and I have almost no experience using static IP under Ubuntu.

A suggestion might be that you could use address reservation through your Router, which will always give your Ubuntu box the same IP matching its MAC address, while still enabling you to use DHCP (might seem pointless, but I would do this because it simplifies the process of getting a connection and keeping it). It should just be in the web interface under LAN settings or something.

---

### Post by ZBlach on 2005-09-30
Output of "sudo ifdown wlan0 && sudo ifup wlan0":

""

No output given

Being as how neither DHCP nor Static seem to be working, we can safely assume that, as of this point, they have no bearing on functionality.

I've spent a few days on this with no success. I'm stuck.

-Z

---

### Post by tehwa on 2005-09-30
Don't give up :eek: 

First, lets have another bash at DHCP, just to get a connection happening:

Paste into /etc/network/interfaces:

```
auto wlan0
```
and comment out```
iface wlan0 inet static
wireless-essid Blacher
wireless-key $MY_KEY
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1
auto wlan0
```
Then disable WEP encryption temporarily to rule out a WEP problem (if possible).

Then go through the GUI under System > Administration > Networking adn choose DHCP, leave the WEP field blank and type the ESSID.

Activate the connection and try to ping your router. If this doesn't work, we'll assume that the card needs some tweaking.

---

### Post by ZBlach on 2005-10-01
I can't disable WEP b/c i'd have to reconfigure it on the other computers. Besides, it worked fine with WEP two weeks ago (since then I've had to replatform. Some failure during the dist-upgrade)

But there has been a change since I last posted. 

iwconfig wlan0 now does not report a connection to an AP. Essid reads: off/any

Still reports a perfect signal tho'

-Z

---

### Post by tehwa on 2005-10-01
i'd like to say a lot of words that aren't allowed on ubuntuforums. instead, illsuggest that you repost your question in networking and state that IP needs to be static, your using breezy, your NIC model and whether you have setup the card using ndiswrapper or whether it is supported natively.

---

### Post by ZBlach on 2005-10-02
wow.

lemme try to explain my situation further.

I'm using Breezy (09/09 release, unable to upgrade as of yet)
I'm using NDiswrapper for a supported card with the appropriate linux drivers
The Network worked fine for my previous router.

My network settings are identical to those in my windows setup, and yet it works fine. I'm typing from a laptop not a metre from my ubuntu box, and i'm getting a flawless signal.

My main concern at the moment: I am unable to associate with my access point. How can I correct this? The manufacturers of my router refuse to offer support, and I've been unable to resolve this myself.

-Z

---

