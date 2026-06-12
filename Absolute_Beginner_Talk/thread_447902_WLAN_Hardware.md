---
title: "WLAN Hardware"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by georgecoffey5 on 2007-05-18
I had a NetGear WG511T Wireless card. 

Since my router displayed a red light(which means no Internet).

So I bought myself a new one LinkSYS card. The very same. I was told by a friend that he doesn't think that any of these will work. 

I'm using Ubuntu 6.06 on a DELL Inspiron 5160. 

I reinstalled Ubuntu no luck.

---

### Post by fastpakr on 2007-05-18
I'm a little confused here...  The router indicated that it had no WAN connection, so you replaced the wireless card?  Something's not adding up.

---

### Post by georgecoffey5 on 2007-05-18
> **fastpakr said:**
> I'm a little confused here...  The router indicated that it had no WAN connection, so you replaced the wireless card?  Something's not adding up.

Basically when the Router displays a red light, it means that the internet is not available, however the Wireless Network Card won't detect or let me surf the internet

---

### Post by chamberlain2006 on 2007-05-18
So the router doesn't have an internet connection?  Maybe you should use an ethernet cable to connect to the router, and navigate to the router config page (usually something like [http://192.168.0.1](http://192.168.0.1)).  Then see if the configuration is ok.

---

### Post by sanjito on 2007-05-18
well, I would think that if your router is giving you a red light, meaning no internet it would mean
a) router is bad
b) outage
c) simething else strange

You would not be able to browse if you had no internet, so your wireless card would not have been bad. meaning you would not have had to replace. and reinstalling ubuntu would not have fixed the problem. If possible, borrow a router from a friend and sii if theirs works. if so, the problem lies in your router

---

### Post by georgecoffey5 on 2007-05-18
The router is back up and running. Other computers is working. 

Just the laptop

---

### Post by fastpakr on 2007-05-18
Are you able to connect to the wireless network and ping the router?

---

### Post by georgecoffey5 on 2007-05-18
How would I do that. I'm completletyl new.

---

### Post by fastpakr on 2007-05-18
You can go to the terminal and type 'ping' followed by a space and the ip address of the router.  You can also right click on the connection icon in the system tray and go to 'Connection Information' to see the IP address you've leased as well as the gateway info (under 'default route').  Have you done anything to actually make the connection to the router in Ubuntu?  You really need to tell us more on exactly what you've done and what you're seeing.

---

### Post by georgecoffey5 on 2007-05-19
Previously I was able to get Wireless Internet, and all of a sudden I can't get it now. I'm now at present using Ehternet(Wired) instead of the Wireless. I even reinstalled it. Nothing

---

### Post by georgecoffey5 on 2007-05-19
Terminal says Network is unreachable
Connection properties does not detect the card at all. 

I have 2 network devices:

ETH0 is the Ethernet(This works great)
ETH1 is the Wireless connection. (This did work before, Not now even after reinstalling Ubuntu).

Would Upgrading to 7.04 be any good.

---

### Post by fastpakr on 2007-05-21
Has it ever worked since you replaced the wireless card?  If not, perhaps you should look the card up to see if it's supported.

---

### Post by georgecoffey5 on 2007-05-27
> **fastpakr said:**
> Has it ever worked since you replaced the wireless card?  If not, perhaps you should look the card up to see if it's supported.

The card has never worked. However I did have the NetGear Wireless card working when I iniallty installed Ubuntu. However recently that gave up and so the new one doesn't work at all. I was told that Linux is not supported out of the box. 

I'm gonna try and put Freespire on instead and see does that do the trick, however in my opinion I think my PCMCIA Card on the motherboard has dies, I may have to get a replacement motherboard. 

For some strange reason my USB Wireless Network card won't work either, and yet I can still use my USB Mouse and USB Memory Key (2GB). 

I'll be talking to Dell over the next week.

---

