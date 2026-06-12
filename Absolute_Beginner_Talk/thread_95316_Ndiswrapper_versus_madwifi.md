---
title: "Ndiswrapper versus madwifi"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by adam.tropics on 2005-11-26
I realise that madwifi is native to Linux and from that perspective the preferred choice, but for my purposes, with constantly playing with fglrx ATI drivers, ndiswrapper fast becomes a viable option.

My question is this. Other than the reasons given above, is there much of a benefit in madwifi? (over ndiswrapper) From my current standpoint, ndiswrapper really seems a perfectly acceptable alternative, speed is about same, and I haven't noticed any performance loss.

Whilst I will keep trying to figure out where my problems are with madwifi, the rush is now off, as ndiswrapper is currently doing a stellar job in its place. Thankyou by the way for everyone who tried to help with madwifi. To be honest, I think i need to clear it from my mind for a few days then come back to it. But like i said, no rush, as now i have options!!

---

### Post by ssam on 2005-11-26
if Ndiswrapper works for you then be happy with it.

some people need opensource drivers for various reasons. eg non x68 hardware.

---

### Post by Kyral on 2005-11-26
I think Madwifi is only for Athereos chipsets anyway. (Anyone wanna correct me on this?)

---

### Post by adam.tropics on 2005-11-26
Well I may have jumped the gun.....again!!

It does work, and work well....But!....
each time I restart the computer, configuring network services takes about a week (! even though eth0 is disabled, just wireless to setup). When I log in, the wireless icon says i am connected, but the device is 'idle'. sudo dhclient gives up, and the only way I have found to get back online is to open up 

Connection properties  --> configure -->select wlan0 -->properties -->change keytype to ascii (even though i have wep disabled!) --> OK-->wait a week -->OK...then we're good to go!

Now I'm glad it works..but seriously, there has to be a more efficiant way! I want it started and running with the computer, so the module is in /etc/modules (hence it does make an effort!)

Any help gratefully recieved....

---

### Post by ShakingSpirit on 2005-11-26
What does '/etc/network/interfaces' look like? Is all refferance to WEP disabled? Have you tried setting a static IP insted of using DHCP?

---

### Post by adam.tropics on 2005-11-26
> mapping hotplug
	script grep
	map eth0

iface ath0 inet dhcp
wireless-essid default

auto ath0

iface wlan0 inet dhcp
wireless-essid default

auto wlan0


So should i edit out that which is not wlan related?
Haven't tried static ip yet.

---

### Post by adam.tropics on 2005-11-26
Ok so far this is where i am:

All the above worked, startup is much much faster, network is configured and clock sync works. But when i log on, i still have to go into configure network settings and make it start work. I have static ip now, so does that mean i should only have the one gateway listed under network settings -->dns ? currently i have the router, but then also 10.0.0.138

---

### Post by adam.tropics on 2005-11-27
Ok i think i've got it......touch wood.

Set to static ip, was nearly there, not quite.
Uninstalled wi-fi radar....for some reason that seemed to clinch the deal. I have absolutely no idea why it worked though!!

---

### Post by adam.tropics on 2005-11-27
Here we go again!!

If left idle for 'a period of time' it goes off again. Upon restart all back as should be. Is there a timeout somewhere i don't know about?

---

