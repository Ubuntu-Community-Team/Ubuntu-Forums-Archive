---
title: "bcm4318 with 6.10"
date: 2007-03-04
forum: Apple PPC Users
---

### Post by eschmidt90 on 2007-03-04
I am running edgy on an iBook G4

I am trying to get my wireless up and running

as it turns out, I can connect to the internet wirelessly, but there's a huge hassle in that I have to manually type the ESSID of the network to which I am trying to connect

I am running NetworkManager, and it recognizes when I plug into a wired connection, but it won't let me view wireless options

how do I a) allow the admin Networking tool see other netowrks or b) allow network manager to see wirelessly

I have searched google extensively, in case you're wondering, and eveything I turn up either doesn't work with edgy, or doesn't work with ppc

any help is greatly appreciated

TIA

~Erik

________________________EDIT___________________________________

It turns out I can no longer connect wirelessly at all, so, now what?

---

### Post by ditsch on 2007-03-10
Can you see your network when you do ```
iwlist eth1 scan
``` in a terminal?I think network manager has some problems if SSID is disabled, so please check that SSID of your access point is enabled.

---

