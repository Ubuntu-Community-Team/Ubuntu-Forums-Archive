---
title: "High processor utilization when running BitTorrent"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by apkolev on 2006-09-20
Hi!

I just installed Ubuntu two days ago and I am very happy with it. I managed to fix most of the things I wanted but I noticed something that I could not find solution for in the forum. 

When I start BitTorrent to download a torrent file, the System Monitor indicates that the processor utilization is around 60 %. I checked the processess that cause this and I saw that "Xorg" is using about 10-25% and "gnome-btdownloa" is using 25%. My processor is Duron 800 MHz. I know it is old and slow but 50% for the torrent download seem too much for me.

Do you have any suggestions how to fix this or did you have any experience like that? Thanks for the answers!

Just a remark: I saw a couple of threads that say that the download is very slow with the biult in Ubuntu BitTorrent. I use the same and I utilize my connection to 100%. I have no firewall or antivirus installed.

Cheers!

---

### Post by Miademora on 2006-09-20
Bittorrent is written in Python. Python has a really high overhead. For a system so slow id suggest using [ctorrent]("http://ctorrent.sourceforge.net/") wich is written in C. My cpuload dropped from 40% to 5% on average per torrent. It doesnt have u gui however.

---

### Post by protohunter on 2006-09-20
Although I can't really help you I have a Duron 850mhz and still use it (wow mainly for games) lol

AMD owns!

---

