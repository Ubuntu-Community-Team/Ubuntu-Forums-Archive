---
title: "i see the light now: ubuntu is the best ... but i don't have network"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by Imre Mehesz on 2006-06-12
hello everybody,

after about 10 different kinds of installation i finally ended up with the ubuntu 6.06 alternate CD ... and it works like a dream...

i even can see my little light on my PCI (laptop) wireless card.. .YAY (never happened before!)

it even says that: network connection: lo ... but i still cannot go to the internet (i cannot even ping ie.: ping [www.google.com](www.google.com) )

in my /etc/network/interfaces i'm missing wlan0 (i think)
[I]#The loopback network interface
auto lo
iface lo inet loopback[/I]

---- and that's all

but if I try iwconfig, i got this:
*lo no wireless extensions*

[I]wlan0 IEEE 802.11b+/g+ ESSID:"STAEDFE34" NICKNAME:"acx v0.3.21"
[etc.etc.etc...][/I]
[I]
sit0 no wireless extensions[/I]

actually, my ESSID supposed to be my router??? (because my router name is not STAEDFE34! ) where can I modify this?

thanks for your help:

eMzMiM

---

### Post by az on 2006-06-12
System - Administration - Netwrork.

---

### Post by Imre Mehesz on 2006-06-12
i have an exclamation point on the two little monitor screens (next to the clock), when I click on it the connection properties: wlan0 pops up saying:
name: wlan0
status: disconnected

Activity
Received: 0 packets (0.0b)
Sent: 0 packets (0.0b)

Signal Strength
going up and down but basically between 78-90% 

when i go system/administration/networking
wireless connection
the interface wlan0 is active

i don't see the little link led blinking on my card (just the power led is on!?)

my network doesn't have any keys ... (WEP or anything)

thanks for your help...
eMzMiM

---

### Post by Imre Mehesz on 2006-06-12
here again,

still not working :( i checked in here:
/etc/network/interfaces 
[I]#the loopback network interfaces
auto lo
iface lo inet loopback

iface wlan0 inet static
address 192.168.1.103 (i set this up)
netmask 255.255.255.0
gateway 192.168.1.1 (this is my router)
wireless-essid linksys

auto wlan0
[/I]

everything looks fine, but i still see the "!" on the two little monitor screen, and the properties say the **status is disconnected**!?

but i have signal strength and everything...
and when I go to configure it says:
*The interface wlan0 is active*

so i donno... i did research but couldn't find solution. i know it is something... very little set up thing (and hope too ;) )

thanks

---

