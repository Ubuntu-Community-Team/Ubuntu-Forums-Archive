---
title: "can't ping, no samba"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by paradoxchild on 2008-02-19
Ever since I've upgraded to gutsy I haven't been able to get samba working again except for one time but it died right after that. I've found out that for some reason I can't ping or be pinged by anyone but I can connect to the internet (as I am doing right now) and other devices can ping each other. I am not using a firewall like firestarter or anything and the router is not blocking me. I've tried reinstalling samba a ton of times and following the guides. I have ipv6 disabled as well. The computer using dapper can access others (except for this computer) through samba. I've read through every related post (and unrelated) that I could find and none of them helped, some of them weren't even ever solved.

---

### Post by neurostu on 2008-02-19
try 
```
$ifconfig
```
what does it put out?

---

### Post by HermanAB on 2008-02-19
Samba is a high level networking system.  It won't work if the basic network setup is all wrong.

So, ensure that each machine has an unique IP address in the same subnet, that they all have the same subnet mask, the same default router and the same DNS setup.  Then ensure that all have the same Workgroup setting and that each machine has a FQDN.  Once all of that is correct, your problems should go away.

If you have a home router, then doing most of the above will be as simple as doing DHCP release and renew on all machines on the LAN.

Cheers,

Herman

---

### Post by paradoxchild on 2008-02-21
Sorry to waste your time but it works now, along with i can ping. I reinstalled iptables, and a few other things along with followed guides for samba. It finally works after restarts, thanks anyways.

---

