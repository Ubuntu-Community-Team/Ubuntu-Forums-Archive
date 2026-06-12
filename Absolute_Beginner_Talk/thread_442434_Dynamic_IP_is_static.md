---
title: "Dynamic IP is static?"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by ltk5 on 2007-05-13
I have a dynamic IP. I'd like to make it somewhat static, because I'm getting more and more interested in servers and server thingies ;)

Any ideas if a thing like this is even possible?

---

### Post by MoxJet on 2007-05-13
If you want to make your LAN address static, you can read howto at [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) under SSH.

If you want to set up a server over WAN, as in having a web address point to your dynamic IP address, you might want to try a combination of DynDNS, [http://www.dyndns.org](http://www.dyndns.org) and ddclient, [http://ddclient.sourceforge.net/](http://ddclient.sourceforge.net/) 

Start the ddclient on one computer (preferably one that is always running), and it will update your DynDNS account. Then you can add addresses you want on your DynDNS account, such as username.homelinux.org, and whenever you go to that address, it will resolve to your dynamic IP... updated from ddclient.

Search around, and try. I set mine up, took some tweaking but it was good fun!

Good luck!

---

### Post by getaboat on 2007-05-13
I'd go for static IP every time.

---

### Post by ltk5 on 2007-05-13
> **MoxJet said:**
> If you want to make your LAN address static, you can read howto at [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) under SSH.

If you want to set up a server over WAN, as in having a web address point to your dynamic IP address, you might want to try a combination of DynDNS, [http://www.dyndns.org](http://www.dyndns.org) and ddclient, [http://ddclient.sourceforge.net/](http://ddclient.sourceforge.net/) 

Start the ddclient on one computer (preferably one that is always running), and it will update your DynDNS account. Then you can add addresses you want on your DynDNS account, such as username.homelinux.org, and whenever you go to that address, it will resolve to your dynamic IP... updated from ddclient.

Search around, and try. I set mine up, took some tweaking but it was good fun!

Good luck!
Whoa:D! So a thing like this really is possible? Sweet:D:lol:
I'll definitely give it a try. [note to myself: before trying a thing like that be sure to buy your 233mhz cumputer an ethernet card.. and don't be to confident, that the 233mhz will really run anything:)]

---

### Post by graigsmith on 2007-07-15
and if you have a router that is upgradable to an open source router firmware such as ddwrt, or tomato router firmware.  then you can have your router update your dynamic dns instead of using software on ubuntu..    i went with the tomato firmware on my buffalo router. and it's completely awesome now.  just be aware. if your router isn't supported by the firmware, OR if you mess up the flashing process. you COULD turn your whole router into a worthless piece of garbage.  be very careful when you flash a routers firmware.  as careful as you would be while flashing a computer's bios.

---

