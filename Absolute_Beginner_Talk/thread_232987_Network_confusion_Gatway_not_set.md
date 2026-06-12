---
title: "Network confusion: Gatway not set?"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by PixelPixie on 2006-08-09
Ok.  I've been looking through this forum all day trying different things and still can't get my network settings to work.   ](*,) 

I can't connect to my machine remotely and I can't ping other machines or view web pages.  I can't access the machine from outside this subnet.  I can access the machine from outside of 18.x.x.x

I want to use:
IP 18.85.28.33
Default Gateway 18.85.28.1
Subnet Mask 255.255.255.0

These numbers are set properly in etc/network/interfaces.  They also show up in ifconfig.

If I do route -n then the destination shows up as 18.85.28.0 and the gateway is 0.0.0.0

If I go to System>Administration>Networking all the settings are o.k., except even though my eth0 connection is active the little dropdown menu that says tho choose a default gateway device is either greyed out or won't stick to eth0.

Help!! :confused:

---

