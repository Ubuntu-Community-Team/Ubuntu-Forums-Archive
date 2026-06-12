---
title: "Firestarter or Guard Dog?"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by houseisland on 2006-07-30
Hi.

In the Package Manager I see what looks like two firewalls, Fire Starter and Guard Dog?

Any preferences or caveats?

Thanks.

---

### Post by cstudent on 2006-07-30
I use Firestarter. I haven't tried GuardDog in Linux, but I did try it in Windows several years ago. Firestarter is a GUI frontend to the iptables. You just open it, set things the way want and close it. It runs silently in the background and does it's thing.

---

### Post by T700 on 2006-07-30
Both of those are graphical interfaces for the same firewall--the one built into Linux.  I find that Firestarter is a bit simpler to set up, but if you want to customize it for particular protocols or needs, it requires more manual effort.  Guard Dog takes a bit more time initially, but can be more easily customized.

The real questions is, do you need either?  Unlike with Windows, unless you are running a server, a firewall doesn't provide much, if any, additional security.  By default, all unnecessary ports in Ubuntu are shut, even with no firewall.  If you are behind a NAT enabled router, you have a double level of protection.  That said, there is nothing wrong with enabling the firewall, it just is unlikely to be needed.

Paul

---

### Post by compuguy1088 on 2006-07-30
Well I've used firestarter, which is basically a GUI backend for IpTables, and it seems to work for me, though I haven't tryed adding any rules and such, but for inital configuration, it is a snap. I haven't heard of Guard Dog, but I should take a look at that as well...

---

### Post by nalmeth on 2006-07-30
I prefer Guarddog. 

I *think* guarddog is QT, and firestarter is GTK. So guarddog is meant for KDE, and firestarter for gnome.

Someone correct me if I'm wrong.

Even when I used gnome I used guarddog, extra libraries weren't that cumbersome at all.

---

### Post by houseisland on 2006-07-30
Thanks all.

For the moment I went with Firestarter.  Very easy setup for basics, which is all that is needed, if a firewall is needed at all.

---

