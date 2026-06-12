---
title: "set mtu for wireless?"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-11-13
I need to limit my maximum bandwidth. In opensuse I could set the mtu easily with a gui. If there is a program like that hand it over.

I want to set mtu for wireless.

I have tried
```
sudo ifconfig wlan0 mtu 700
```
but it didn't work.

Any ideas?

---

### Post by tdrusk on 2007-11-13
bump

---

### Post by tdrusk on 2007-11-13
weird. I did it again and it worked.

---

### Post by Austin_KW on 2007-11-13
How would that limit your bandwidth, the fragmentation would slightly increase you bandwidth usage?

---

### Post by tdrusk on 2007-11-13
> **Austin_KW said:**
> How would that limit your bandwidth, the fragmentation would slightly increase you bandwidth usage?

It didn't actually. I was wrong.

What can I do to do this?

---

### Post by poudin on 2007-11-13
in other distros u would just append

MTU=xxxx

 to /etc/sysconfig/network-scripts/ifcfg-ethx

than restart the interface with ifdown etho ; ifup eth0

not sure what the equivalent config file is in Ubuntu...let me do some checking

---

### Post by poudin on 2007-11-13
[http://ubuntuforums.org/archive/index.php/t-3985.html](http://ubuntuforums.org/archive/index.php/t-3985.html)

check this site...they wrote a bash script to set the MTU and put in /etc/if-up.d...and it should get called on startup

ifconfig eth0 should show the new MTU if it got set correctly

---

### Post by Austin_KW on 2007-11-13
What are you trying to  achieve?
It sound like traffic management or traffic control (tc) i.e. settings limits on totals and different types of traffic.

This is usually done if you build yourself a router. From memory you might want to look at shorewall. It is a firewall and I think that it has a GUI for traffic control.

---

### Post by poudin on 2007-11-13
setting the MTU will adjust the packet size used...we had to change it at work a few times to get some slower wireless equipment to run in a stable manor...by default...set to 1500....we actually set the max value to 1300 and noticed that the performance of the equipment was improved.

---

### Post by tdrusk on 2007-11-13
> **Austin_KW said:**
> What are you trying to  achieve?
It sound like traffic management or traffic control (tc) i.e. settings limits on totals and different types of traffic.

This is usually done if you build yourself a router. From memory you might want to look at shorewall. It is a firewall and I think that it has a GUI for traffic control.

when I upload or download I take away connection from the other computers on my network .

---

### Post by poudin on 2007-11-13
the issue u described sounds like using all the bandwith u have..you might want to cap you DL/UL speeds if u need to have the other computers...or consider setting the scheduler in your software and do your DL/UL when everyone is sleeping.

I don't think changing MTU settings will fix your issue.

---

### Post by tdrusk on 2007-11-13
> **poudin said:**
> the issue u described sounds like using all the bandwith u have..you might want to cap you DL/UL speeds if u need to have the other computers...or consider setting the scheduler in your software and do your DL/UL when everyone is sleeping.

I don't think changing MTU settings will fix your issue.

okay. How can I cap my speeds?

---

### Post by poudin on 2007-11-13
usually in the software u are using u can set max DL limit and max UL limit...just depends what u are using...i assume you are talking about bit torrent software

i use qBitorrent and u can set the limits per download item..

---

### Post by Austin_KW on 2007-11-13
> **tdrusk said:**
> when I upload or download I take away connection from the other computers on my network .

Yes, that is traffic management or traffic control. But usually you want to do the traffic control on the router or gateway where all the traffic gets merged.  Most consumer routers will not allow you to do this, you could build a linux router but it is not a trivial project.

You may be able to run traffic control on your own PC and just limit the bandwidth that you allow for your internet connections. The problem is that this would be a hard limit, e.g if you only ever allow your PC to use 50% of your internet bandwidth then this limit will still apply even when the other PCs are idle.

The other option is to use a torrent client that will do the limiting but this would have the same issue with hard limits.

---

### Post by jaybombalous on 2007-11-13
what are u d/l'ing that consumes that much network interface? What are u uploading?


I have experienced this with torrents, I reduced my number of connections from 375 to 225 and things worked like a charm.

---

### Post by intelligentfool on 2007-11-13
[http://en.wikipedia.org/wiki/Maximum_transmission_unit](http://en.wikipedia.org/wiki/Maximum_transmission_unit)

> A higher MTU brings higher bandwidth efficiency.

if the main application your having issues with is using a particular protocol (say torrent, TCP @ 6881-6999) you could play with the QOS settings on your router if it has that feature. otherwise, the other suggestions seem like your best bet (throttle the B/W in the app itself, or setup a linux router so you can run QOS)

---

### Post by tdrusk on 2007-11-14
It's when I download large packages such as ubuntu-desktop and upload pictures and videos online.

---

