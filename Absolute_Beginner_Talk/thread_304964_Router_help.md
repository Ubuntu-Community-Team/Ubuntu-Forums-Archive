---
title: "Router help"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by nonpareilpearl on 2006-11-22
So I found out why my connection is so slow. I live on a University  campus (in an apartment) and use their DSL to connect. ResNet (the campus network) "does not like" Linux packets, and when I emailed my listserv at work, after trying the various fixes (arp, disabling ivp6, adding the "ResNet" fix and etc.) they said that the quickest and easiest way to do this is to buy a router and just prevent the linux machine/s from "talking" directly to ResNet. So far I have been given three options for routers: a DLink, Linksys and NetGear.

Slickdeals has a D-Link DI-624 Xtreme G Wireless Cable/DSL Router for cheap, I heard that Circuit City might reduce the price on the router, but I heard that this Linksys works really well with Linux in general. But the deals that I have found so far expire 11/30 so please let me know if any of them work particularly well with Linux (for reference the reason I was looking at wireless routers is because I have a laptop and a desktop and I want to network them together as well).

---

### Post by JShadow on 2006-11-22
Any router should work fine, as it's not really OS specific. Although I once had a D-Link gateway that could only be administered with Internet Explorer. Personally I've had better luck with Linksys brand.

As far as your actual problem, "not liking linux packets" doesn't really seem to make sense. Is it just browsing the web that is slow? I've had experiences where there was a slow DNS response, and installing BIND to cache locally made a world of difference. You may want to try that before you go out and buy hardware. Take a look at [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto) under the caching.

---

### Post by Tilex on 2006-11-22
Please someone correct me if I'm wrong but I don't think your Operating System makes a difference on the router.  I mean, your ethernet card talks to the router, and communicates with your kernel via device drivers, so as long as Linux understands your device, it won't affect your router's functionality whether you're on Linux or Windows....
As far as the routers are concerned, my experience would advise NOT to buy the D-Link DI-624 router for I have bought 2 in the past and they both broke up after 1 year each.  I now own a Linksys (which is owned by Cisco) and it works very nicely with loads of options on it.  I don't know anything about NetGear, though.

---

### Post by nonpareilpearl on 2006-11-22
I didn't post the link to the Linksys, but it's the [WRT54GL]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1820385&CatId=0"). I understand that routers are OS dependent, although I hear that since this uses Linux firmware it will support things like BitTorrent and lets you prioritize that packets that are sent (i.e. if someone is downloading something, vs. you wanting to surf the web, you can prioritize it). I was really wondering which of the routers has the best longetivity and etc., only because the reviews on different sites seem very mixed.

---

### Post by mssever on 2006-11-22
I use a WRT54G and havent been terribly imressed, but then its the only one Ive used. Its configuration ages dont look good in browsers other than IE, and dont work at all without javascrit. elinks comes to mind.


Also, it isnt Linux based anymore, due to the restrictions of the Linux license. They dont want to make their source code available.

BTW, in case you were wondering, several keys on my keyboard have died. Thats why some letters are missing.

---

