---
title: "aMule port 4662 closed: lowID"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by ivuntu on 2006-03-10
Hello all,

I read several hreads related to this, but could not find the answer to my problem.:confused: 

 I am trying to use aMule, but I get a lowID.
 I opened ports 4661, 4662, 4665, 4672 in the 'Allow Service' part of Firestarter. The "Forwarding service" is not accessible (greyed out).
This does not seem to have any effect, the TCP/UCP test on [http://www.amule.org/testport.php](http://www.amule.org/testport.php) gives a time out error on port 4662.

Also, when I disable Firestarter, I still get a lowID!

Can anyone tell me what the problem could be, and how to fix it to get a highID?

Thanks very much in advance!

---

### Post by meborc on 2006-03-10
when i tackled the same problem, i found that although all ports were opened on my side, my internet provider had some of them closed... ;) for legal issues... so there was nothing on my end to do... try getting info from your internet provider

---

### Post by mlind on 2006-03-10
if your isp is blocking default port, p2p apps usually allow you to change this port
for another.

---

### Post by ivuntu on 2006-03-10
[QUOTE=mlind]if your isp is blocking default port, p2p apps usually allow you to change this port
for another.[/QUOTE]


I tried setting the port in AMule to 4688 and opening the incoming port 4688 in Firestarter also, but I doesn't work: still low ID :( 

Maybe any other ideas?

---

### Post by mlind on 2006-03-10
[QUOTE=ivuntu]I tried setting the port in AMule to 4688 and opening the incoming port 4688 in Firestarter also, but I doesn't work: still low ID :( 

Maybe any other ideas?[/QUOTE]

aMule client will also need port open for UDP 4672 for kademilia support.
LowID issues are probably covered better on [eMule's faq]("http://www.emule-project.net/home/perl/help.cgi?l=1&rm=show_topic&topic_id=308").

---

