---
title: "Package Data Storage"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by BitTorrentBuddha on 2006-08-22
Hey, I was just wondering, for hard-drive partitioning concerns, where the majority of the data for packages downloaded is kept, I assume somewhere in /var or something of the sort? Also how much does the package data take up space wise? What would be a reasonable sized root partition for my new 200gB hard drive (putting /home and /opt on different partitions)?

---

### Post by simonn on 2006-08-22
> **BitTorrentBuddha said:**
> Hey, I was just wondering, for hard-drive partitioning concerns, where the majority of the data for packages downloaded is kept, I assume somewhere in /var or something of the sort? Also how much does the package data take up space wise?



Packages management info in /var/lib/dpkg (18.6886Mb at the moment on my system)

Packages (.deb files) are cached in /var/cache/apt (196.339mb at the moment on my system). 

> What would be a reasonable sized root partition for my new 200gB hard drive (putting /home and /opt on different partitions)?

IME somewhere between 5-8gb is fine for /

I include /opt and most of /var on the same partition as /, but use a seperate /tmp partition  - 2Gb which is excessive, but was easy for me to setup without using disk destr^H^H^H^H^Hpartitioner like gparted and I have close to 1TB of disk space so 2Gb ain't nuthin.

EDIT: remember that with unix/linux if you find you are running out of space on /, you could always move, for example, /var or /tmp to another paritition.

---

