---
title: "Ktorrent not connectable after a time"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by lespaul_rentals on 2007-10-10
I have a very interesting problem.  I am a member of a private tracker that has shows if someone is "Smart."  Being Smart means you have your ports forwarded and your client configured correctly and can accept incoming connections, thus being an efficient seeder.  I use Ktorrent and am very happy with it, however, there's one problem.  When I initially start Ktorrent, I can seed very well, and the tracker says I am connectable/Smart.  However, after about 15 minutes, my status suddenly changes to Not Smart.  All uploads that start beforehand will still continue to transfer, but I can't accept new connections or they are very slow.

Now, the way to remedy this is to restart Ktorrent every 15 minutes or so, but I would like to seed for the community 24/7, taking advantage of the reliability of Linux.  ;)  Let it be noted that:

I have forwarded the appropriate ports.
I have configured Ktorrent correctly.
I have enabled UPnP in Ktorrent, and it recognizes that port 5001 (the port I forwarded) is open on the router.
I am initially connectable for about 15 minutes, then it suddenly drops, whether I am using the Internet or not.  Downloads will still be going, but uploads will slow and eventually drop.
I do not use a firewall.
The same router settings/ports worked for me back with uTorrent/XP.

Any ideas?

---

### Post by Dr Small on 2007-10-10
If you use Ubuntu, you do use a firewall.
You need to configure firestarter too.

---

### Post by lespaul_rentals on 2007-10-10
I have turned Firestarter off.  If by "you do use a firewall" you mean iptables, why would this problem arise 15 minutes after starting Ktorrent and not initially?

---

