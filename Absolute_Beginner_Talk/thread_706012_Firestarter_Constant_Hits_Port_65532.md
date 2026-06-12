---
title: "Firestarter Constant Hits Port 65532"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by seeking_alpha on 2008-02-24
To get green "NAT ok" in Azureus, I enabled port forwarding on my router and put a policy in Firestarter to allow connections on port 65532 for anyone.

When I removed that policy on firestarter, I started to get constant hits on that port, as in every second, from all sorts of ip addresses, even when I am not running Azureus. I also turned off port forwarding on my router but I am still getting hit constantly on that one port. 

Is this something I should be concerned about? Does that mean when I put in the allow policy in firestarter I'll be accepting all of those connections even with Azureus off? :confused:

---

### Post by mikewhatever on 2008-02-24
> **seeking_alpha said:**
> To get green "NAT ok" in Azureus, I enabled port forwarding on my router and put a policy in Firestarter to allow connections on port 65532 for anyone.

When I removed that policy on firestarter, I started to get constant hits on that port, as in every second, from all sorts of ip addresses, even when I am not running Azureus. I also turned off port forwarding on my router but I am still getting hit constantly on that one port. 

Well, you closed the port, so what did you expect?

> Is this something I should be concerned about? Does that mean when I put in the allow policy in firestarter I'll be accepting all of those connections even with Azureus off? :confused:

Yes, so it seems, but with closed port, there is nothing to worry about. Just curious, does Asureus not open its port automatically?

---

### Post by seeking_alpha on 2008-02-24
Well it wasn't happening before I opened the port, so thats why I thought it was weird.

---

### Post by hyperair on 2008-02-24
After closing a torrent and a port, it usually registers connection attempts for a while more untli the tracker notices you're not there any more. More importantly you should check the IP addresses. Where are the connections coming from? Inside or outside your networK? If it's outside your network, you should check again your port forwarding settings for the router.

---

### Post by seeking_alpha on 2008-02-24
It's comming from outside Lithuinia, Italy etc. I disabled port forwarding and UPnP, but still the hits keep comming. I just set firestarter to ignore events from that port.

Quick question though, will all this "hitting" degrade my internet speed?

---

