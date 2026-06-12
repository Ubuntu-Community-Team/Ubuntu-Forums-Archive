---
title: "downloading torrents slows connection drastically, even at 2kb/s"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by Fittersman on 2007-09-16
for some reason, when my brother downloads torrents on the other computer it will slow my computers wireless internet connection down to a crawl (its even worse than dialup). It doesnt seem to matter how fast his torrents are downloading at because it slows it down to about the same speed anyway.

why does a 2kb/s torrent download use up all the bandwidth? (the upload speeds are really slow too)

o yeah, and if he downloads using like firefox or something, i wont even notice it.

---

### Post by jordanmthomas on 2007-09-16
bittorrent opens a **lot** of connections.  My router (a linksys WRT54G) has problems with too many connections and the same problems you describe arise.  Oddly, though, the connection does not get slow on the machine that is *doing* the torrenting...go figure.  On the other hand, if you're just using a lot of bandwidth from one connection there's no major problems on either computer.  

So I guess the answer is it comes down to the bittorrent protocol itself and the way your router handles it.  Bittorrent is the destroyer of networks.  You can look around and see if there's any firmware updates for your router that may address the issue or if you're lucky there may be an open-source firmware that actually adds features and gets rid of your problems.

---

### Post by trippinnik on 2007-09-16
What torrent program is he using?  The connection number is probably the problem (as mentioned), all the good programs have controls for number of connections, make is something like 100 or less globally.

---

### Post by Fittersman on 2007-09-17
hes using ktorrent

---

