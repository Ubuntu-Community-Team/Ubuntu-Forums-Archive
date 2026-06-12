---
title: "network manager quit working after patches yesterday"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by BillGod on 2007-04-12
I posted this in network hour and 1/2 went by and only 10 reads and no ideas for a fix  So I will post here also.

Running Feisty Beta

Network manager was working perfect. I had a vpn setup to connect to my MS PPP vpn at work and was working fine. Yesterday a patch came out for it. The second the patch installed my network broke. I was at work using vnc to run the update. When I got home I had no network connection. network manager says "no network connection" when moused over. I checked my network settings and rebooted thinking it was just a glitch. Still no network. Changed my NIC over to DHCP instead of static and the internet was working. Network manager still says no network connection. I removed every trace of network manager through synaptic. then re-installed. If I run nm-applet from prompt I still get same problem. Any ideas on what to check?

Thanks
Bill

---

### Post by zvacet on 2007-04-12
Disabling network manager in the sessions/startup bit and type
```
sudo ifup eth0
sudo ifdown eth0
sudo ifup etho
```

Hopefully other updates will correct mess.

---

### Post by BillGod on 2007-04-12
eth0 is already up..I am on my pc right now connected to the net. network manager somehow quit noticing this fact.  It's almost like network manager doesn't recognize my NIC

---

### Post by BillGod on 2007-04-13
It looks as though something is corrupt on my network drivers.  If I set my ip to static and ping my router I get network unreachable.  Anyone know how to uninstall my NIC and reinstall?

---

### Post by Zdravko on 2007-04-13
[BillGod]("http://ubuntuforums.org/member.php?u=165598"), I have the same problem. Help!

---

