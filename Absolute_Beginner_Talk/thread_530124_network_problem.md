---
title: "network problem"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by mstrap123 on 2007-08-20
i installed ubuntu 6.10 server edition to share file and folder, i installed and configure samba server but i cannot view or ping my server from my xp workstation, i cant ping my xp workstation from my server also. what is the problem ?

---

### Post by nexu56 on 2007-08-20
You can put the samba problems aside for now. If you cant ping, you have a network connectivity issue. 

Are you pinging ip addresses or hostnames?

What IP addresses are you using? 192.168.x.x? 10.x.x.x?

Are you using firewalls on either machine?

---

### Post by HereInOz on 2007-08-20
A firewall I would guess is the problem.

Install Firestarter (in Synaptic) and then you will be able to allow the two machines to ping one another.  When you configure Firestarter, make sure that you go into preferences and then advanced options, and uncheck the option to block broadcasts from the external network.

---

