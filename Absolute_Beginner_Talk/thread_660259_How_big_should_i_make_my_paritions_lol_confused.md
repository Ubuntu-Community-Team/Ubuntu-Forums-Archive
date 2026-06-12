---
title: "How big should i make my paritions? lol confused"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by BOBSONATOR on 2008-01-06
Hey guys, this is a quick response thing.

I have an 80 gig laptop, and want to put arch on it, but i also need windows for some important apps (adobe contribute photoshop, vegas (movie editing a little bit), etc). 

My windows is going to be NTFS, and im going to use reiserfs (i like speed) for linux, all i need linux for is browsing, chat, compiz, some music, downloading torrents. 

How big should i make each partition? or what percentage of my hd should linux be compared to windows in my situation? feel free to ask questions.

Thanks in advance!

---

### Post by PeterJS on 2008-01-06
You can get a way with a pretty small partition with these days because of the ntfs drivers you can off load big files like media on the ntfs partition. 10 gigs for root and swap should be ample. You could probably get away with less if you wanted to but I wouldn't go below 5 gigs for root if you're planning on having root and home on the same partition.

Currently my system is split:
100 gigs ntfs
2 gigs swap
18 gigs Ubuntu

---

### Post by philinux on 2008-01-06
About 15-20 gig should be fine for Linux. Maybe less

Someone else may chime in. you can always use your ntfs partition to store music on too.

---

### Post by BOBSONATOR on 2008-01-06
thanks guys

---

### Post by Shazaam on 2008-01-06
Is this XP or Vista? XP has few problems running on 50 gig or less (depending on what you have loaded up).
When I single-drive multi-booted I gave XP 35gigs; made a 1gig /swap, and used the rest of the free space for 3 flavors of linux. I got so tired of XP crashing and needing to be reinstalled frequently so I broke down and bought another hard drive. Now XP lives happily on an 80gig drive by itself and I installed a 320gig drive for linux. Plenty of room to bash a bunch of distro's around. BTW, all of my linux distro's share a 2gig /swap (probably overkill).

---

### Post by rcsarver on 2008-01-06
Shazaam,
I am dual-booting winxp with ubuntu on a 60gb hard drive with no problems because the winxp partition size.

---

