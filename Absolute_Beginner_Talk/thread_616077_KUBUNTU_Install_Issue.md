---
title: "KUBUNTU Install Issue"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by bobd104 on 2007-11-17
Just finished loading KUBUNTU and unlike other Linux installs, I can't connect to the internet.  Any configuration I try won't give me an online connection?  I've configured the system as :Auto, dhcp.  This is what I did in all other installs and everything worked just fine?  Any suggestions?

---

### Post by wolfger on 2007-11-17
> **bobd104 said:**
> Just finished loading KUBUNTU and unlike other Linux installs, I can't connect to the internet.  Any configuration I try won't give me an online connection?  I've configured the system as :Auto, dhcp.  This is what I did in all other installs and everything worked just fine?  Any suggestions?
Open a command line (Konsole), type "ifconfig -a", and give the results. Also give the results of "route". Are you connecting directly to the internet or is there something in the middle (wi-fi router, etc)?

---

### Post by bobd104 on 2007-11-18
Thank you for your reply but I solved the problem identifying the IP address was not entered in the route?  After manually inputing this address, it seems to work fine. . .:)

Bob D.

---

