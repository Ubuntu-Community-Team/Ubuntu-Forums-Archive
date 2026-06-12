---
title: "How come there's less peers on Ktorrent, Deluge compared to Azureus?"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by dannyboy74 on 2007-09-16
How come there's less peers on Ktorrent, Deluge compared to Azureus?
When you use Azureus there might be some 50-100 peer for a certain kind of file but when you use Ktorrent and Deluge on the same kind of file it seems like the peers only goes from 3-10 or something of such relativity.

Why is that?  I thought that they all used the same p2p network.

---

### Post by AlexenderReez on 2007-09-16
as far as i know azures is java application that allow user to do port forward.....

to get more peer...use

> sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT




and use
> sudo iptables -A INPUT -p tcp --dport 6881 -j DROP

to close it back after done it....

---

### Post by dannyboy74 on 2007-09-16
So that's why... Ktorrent and Deluge are cutting away user with routers from the torrent network.  That's sad I really like those 2 programs in comparison with Azureus/Java :(

---

### Post by stimpack on 2007-09-16
I have no problem with KTorrent, but my ports are setup in the router. afaik Azureus uses uPnP to punch holes through your router, best to do it yourself and disable uPnP, I dont like programs having the power to punch through my router.

---

### Post by MrHippocampus on 2007-09-16
You should also open the bittorrent port to udp aswell as tcp, this allows you to use DHT to find more peers.

---

