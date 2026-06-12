---
title: "How to add another gateway"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by teamworx on 2005-12-10
Hi good day to all, can somebody help me with my problem, it goes like this, I had 2 dsl internet line and each line has its own single wan router, so therefore i had 2 router, and in my gateway i need to put those two router's address, but i found out that ubuntu can only accept one default gateway, is there anyway i can add another gateway? this is just incase one dsl line is down it can tranfer to the other gateway and use the other line. tnx

---

### Post by Lambert on 2005-12-10
Look at this utility called backroute. It's basically a shell script run with cron to monitor one route, and if it goes down it reverts to a second route, and it even continues to monitor and will go back to your original route when it comes back up.

[http://www.epr.ch/brb/linux/backroute.html](http://www.epr.ch/brb/linux/backroute.html)

There may be something else but there is no way to set up two external routes/gateways that I know of. You will need to set up some sort of monitoring method where the routing table can be ameneded if trouble with one route is recognized.

---

### Post by cwaldbieser on 2005-12-10
[QUOTE=teamworx]Hi good day to all, can somebody help me with my problem, it goes like this, I had 2 dsl internet line and each line has its own single wan router, so therefore i had 2 router, and in my gateway i need to put those two router's address, but i found out that ubuntu can only accept one default gateway, is there anyway i can add another gateway? this is just incase one dsl line is down it can tranfer to the other gateway and use the other line. tnx[/QUOTE]
If you wanted, you could even use iptables to distribute the traffic accross the two gateways, but unless you have a script to monitor things in place, if either of the gateways goes down, you will start getting intermittent network errors.

---

### Post by teamworx on 2005-12-11
Thank u sir for your very quick response and for ur time, i really aprreciate both of ur effort, i'll try my best to analyze both of ur sudgestion.

---

