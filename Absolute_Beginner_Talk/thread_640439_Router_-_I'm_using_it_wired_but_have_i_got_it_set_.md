---
title: "Router - I'm using it wired but have i got it set up right"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-12-14
I've a 2wire wireless enabled router but I'm running it wired to a desktop pc. Son had a wireless laptop but he's moved out now. !!! SID broadcast is disabled.

Internets been fine with Feisty and Gutsy. But poking around I find in network settings that Roaming  Mode is enabled. If I click properties there are options for 

Static IP
Auto conf DCHP
Local zeroconf network IPV4

Question is - is it set up correctly? I get network traffic I think from my ISP every 6 or so seconds. Probably a ping but I've no idea about networks.

---

### Post by IgnacioMiller on 2007-12-14
It would appear to be set up correctly to me. Roaming mode doesn't really matter on desktops. You have a working connection to the internet on that computer, right?

---

### Post by philinux on 2007-12-14
Yep net access fine - it was this roaming mode check box that's ticked that had my curiosity going.

The router firewall set up is shown below - I thought that block ping would stop ISP net traffic bit I seem to get something every 5/6 seconds and the pc responds.

---

### Post by philinux on 2007-12-14
Where are all the network guru's ?

---

### Post by OffAxis on 2007-12-14
> I get network traffic I think from my ISP every 6 or so seconds.
That's pretty regular; probably an advertisement on an open webpage or a feed refreshing.
It could also be the connection's 'keep alive' packet, depending on your setup.

You can try pinging your external IP
```
ping -c 4 [your external IP]
```
and see if you get any feedback. Since you've got it disabled they should all die.

You should also have an active connections tab somewhere in there or 'connected devices' listing.

And there should also be an access log in your router that you can check for illicit connections.

---

