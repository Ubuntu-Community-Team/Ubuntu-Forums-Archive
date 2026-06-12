---
title: "connection troubles"
date: 2006-01-30
forum: Absolute Beginner Talk
---

### Post by helrumyc1 on 2006-01-30
Alright, heres whats up. I have 2 computers, both have linux on them, they are (in real life) located RIGHT NEXT TO EACHOTHER, both monitors and both computers are right next to eachother, now heres teh prob. I have a wireless internet connection and (obviously) a wireless router. HOWEVER, I dont have another wireless card for the other computer, what i do have is an ethernet cable that i tried connecting the two computers with. The one with wireless still works but i cant seem to get the second computer to run off of the other computer's wireless internet connection. Is this just simply not possible? or am i doing it wrong? how would i set this up?

thanks for teh help! :)

---

### Post by mips on 2006-01-31
The cable must be a cross-over cable.

Install Firestarter firewall on the wireless pc and configure internet connection sharing.

Ensure the wlan & lan are in different networks.

Ensure the other pc share the same lan settings as the internet enabled one withe exception of the ip address

---

### Post by helrumyc1 on 2006-01-31
okay, so i'm geussing there is a difference from a regular router cable and a cross over cable then? if i get a cross over cable, and connect it to the wireless computers etho slot and into the other computer's etho slot it will work after i set up sharing? Because right now when i tried it said the Etho0  or w/e device wasn't ready or something, either way it didnt work.

---

### Post by mips on 2006-01-31
Yes in theory it should work fine if your ethernet cards work fine.

The cable between the router & PC is usually a straight cable.

---

### Post by helrumyc1 on 2006-02-04
[I]"Ensure the wlan & lan are in different networks.

Ensure the other pc share the same lan settings as the internet enabled one withe exception of the ip address"[/I]


could you explain what you meant by this please? and how i would accomplish it, both computers are running linux if i didnt mention that before. Thanks

---

### Post by mips on 2006-02-04
An example:
Ethernet: 192.168.0.0 255.255.255.0
Wireless: 192.168.1.0 255.255.255.0

If you still get stuck post your TCP/IP config for you different interfaces here.

---

### Post by helrumyc1 on 2006-02-05
Alright, i just got the Crossover cable today, and i have no idea what I am doing. Can somebody please give me step by step instructions on how to set this up. Ill go over what i have again

-One computer with a USB wireless card
-Another computer that currently has no internet connection
-A crossover cable that is now connected in both computers' ethernet slots
-Both computers running Ubuntu with the KDE desktop eviorment
-The computer with the wireless card and the functional internet has firestarter firewall

I need a detailed explination on how to get the computer that doesnt have internet connection set up so that it uses the crossover cable to feed off of the other computers wireless internet connection.

as shown below:
[ (wireless card) ---> Computer A <---(crossover cable)---> Computer B ]

Please give as much information as possible, i'm not good with hardware setup and things of this nature. Thank you :)

---

### Post by mips on 2006-02-05
Please post the /etc/network/interfaces files of **both** computers here. If you are using DHCP post the TCP/IP details of the network here.

I'll edit them and repost.

Right now I'm going to bed but will reply tomorrow.

---

### Post by helrumyc1 on 2006-02-05
COMPUTER WITH WIRELESS INTERNET (COMPUTER A):

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
address 192.168.0.1
netmask 255.255.255.0


iface wlan0 inet dhcp
wireless-essid Wireless

auto wlan0


auto eth0
______________________________________________________________________________
COMPUTER B:

(will be in next post since i have to change over the connection)

---

