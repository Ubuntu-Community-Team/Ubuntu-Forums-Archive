---
title: "What is the best way to build a PC based router and wifi router."
date: 2020-07-10
forum: Any Other OS
---

### Post by Omnios on 2020-07-10
What would the best way of making a small PC router, wifi router, Firewall to learn more about networking? I am thinking of getting a referbed computer and use a 4 port internal switch and possibly use two wireless cards cards for two separate users. I would also like to play with a shell to control it and also possibly a web interface. An important part will be to use the firewall to learn more about it.

---

### Post by TheFu on 2020-07-10
Don't put wifi stuff in the router. Use external APs, like those from Ubiquiti.  Then you can add, upgrade, wifi stuff as desired without being tied to the location of your router.  Routers should normally be inside a locked closet or room.  Wifi-APs are usually installed in a wall or ceiling centrally or on opposite sides of a building to provide barely overlapping coverage.  Not once, anywhere, have I seen the router location also be the best place for a wifi-AP.

If you are paying more than $120 for this old computer, then you are better off going with a purpose-designed router-PC.  I have an APU2 running OPNSense. It previously ran pfSense.  Building your own Linux distro just for routing is usually a fools effort, since few people have the Linux and routing skills to do that securely.  I don't think I could, at least not without leaving something, probably a few things, open to the world, accidentally.  

[https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/](https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/)

But if you don't have lots of time and/or money, it is amazing how great a router from Ubiquiti or MikroTik can be for the price.  Those companies have a good reputation for quickly having patches available. Both were caught improperly using GPL software early in their lives. They come around.  
[https://category5.tv/shows/technology/episode/650/](https://category5.tv/shows/technology/episode/650/) MikroTik video guide part1.

Ubiquiti makes some of the most cost-effective, quality, wifi-APs available, but their routers run an obscure OS.  Their APs are almost always PoE, which makes power and the ethernet connection happen over the same CAT5e cable. It is crazy great when you can finally run power+ethernet from your network closet, through the attic/ceiling tiles, to the center of the house, make a tiny hole and mount the AP exactly where it is best located, looking like a built-in smoke alarm.

MikroTik uses Linux, but it is tempting to buy an all-in-one wifi+router which isn't probably what anyone other than grandma really wants. You can mix Ubiquiti APs with almost any other vendor's routers.  I've replaced netgear wifi-crap with Ubuquiti a few times when the netgear stuff wouldn't maintain connections as many clients showed up. The Ubuquiti AP didn't have issues with 50 clients.  Just sayin'.

There are lots and lots of blogs out there around wifi and networking. Here's 1: [https://www.jeff.wilcox.name/2018/04/seattle-network/](https://www.jeff.wilcox.name/2018/04/seattle-network/)

Sadly, here's my cheap ($114/month), business, connection:
```
Download: 29.71 Mbit/s
Upload: 5.95 Mbit/s
```
I pay for 25/5, so getting more is nice. It wasn't always that way.  I know my APU2 can only handle about 650 Mbps down from my LAN testing. Most of the network is wired GigE. Wifi is for untrusted guests.  That goes for all wifi, all bluetooth, all direct RF stuff. I wasn't always that way, until speaking with some military "signals" experts at security conferences. In short, don't use any wireless connection without a full, strong, VPN, that is managed separately from any network equipment.  But if you are just worried about a 10 yr old little brother, have at it - use any wifi you like.

---

