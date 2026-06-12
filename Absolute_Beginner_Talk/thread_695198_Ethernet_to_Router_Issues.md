---
title: "Ethernet to Router Issues"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by a.swan89 on 2008-02-12
I just got a new router (Linksys WRT54G) and I was eager to try it out, but my computer running Kubuntu 7.1 won't connect to it. I'm on a dorm network and I was getting tired of switching between having my laptop or my desktop connected to the network. My laptop, also running kubuntu, is getting to the internet just fine, but my desktop doesn't even recognize that a cable is plugged in to it. Whats wrong?

---

### Post by Jewfro_Macabbi on 2008-02-12
How is your networking configured? manually or via system - network - network-admin?

check /etc/network/interfaces  - do you have an eth0 or eth1 as it may be entry?

---

### Post by dcstar on 2008-02-12
> **a.swan89 said:**
> I just got a new router (Linksys WRT54G) and I was eager to try it out, but my computer running Kubuntu 7.1 won't connect to it. I'm on a dorm network and I was getting tired of switching between having my laptop or my desktop connected to the network. My laptop, also running kubuntu, is getting to the internet just fine, but my desktop doesn't even recognize that a cable is plugged in to it. Whats wrong?

If your PC doesn't light up the port when you plug a Ethernet cable into the router, you have:
[LIST=1]
[*]Router ports that are not enabled
[*]A bad cable
[*]Your PC network card is not enabled, or
[*]You have a faulty PC LAN hardware
[/LIST]
You need to check all of these.

---

