---
title: "azureus and guarddog"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by mrvgarg on 2006-06-03
Hi

How do I set up guarddog to allow azureus to work?

---

### Post by steve.horsley on 2006-06-03
You need to enable both the BitTorrent Tracker and BitTorrent Peer protocols on the internet. You also need ot enable Bitorrent Peer on our local machine. 

Beware of BitTorrent machines that use non-standard port numbers. You may have to open extra ports if you can find out what numbers they are using.

---

### Post by sparau on 2007-08-10
Hi - dragging up an old thread.

Running feisty 7.04 - guarddog.

As suggested here i have opened up bittorrent on local and internet - and even made a rule to allow port 61495 (as shown in azureus) for TCP and UDP but no go...

if i disable the firewall then - hey presto - azureus happy :(

Any suggestions happily accepted :)

---

### Post by ellgor on 2007-08-10
Hi,

Try using Ktorrent, its easier ( it tells you what port's to open), just as fast and pretty, hope this helps.

Regards, Ellgor.

---

### Post by benn333 on 2007-11-04
Replying to this thread because I'm having the exact same problem as sparau mentions...Azureus works fine with Guarddog disabled, but the bittorrent tracker can't get through with Guarddog enabled. Same thing happens with KTorrent.

I've configured both apps to use port 50000 for TCP and UDP traffic and set up my router to forward the traffic. In Guarddog I've created new User Defined Protocols for the port and permitted the protocol on both the Internet and Local Defined Network Zones. 

Still the tracker connection times out in both apps, which prevents torrents from starting. If I disable the firewall via Guarddog, the tracker connects and the torrent starts. (If I reenable Guarddog the download continues, but the tracker continues to fail on future connections.) Any ideas what's going on here? Everything seems in order, but the traffic keeps getting blocked by Guarddog.

---

### Post by albywolf on 2008-06-15
I ended using firestarter, but still had a problem with the router, so I looked at azureus logs and discovered that it needs to open another port besides the one around 50000 I chose. This other port in my case was 16200, I don't remember exactly what it was needed for, but I guess it must be enabled in guarddog too.

---

