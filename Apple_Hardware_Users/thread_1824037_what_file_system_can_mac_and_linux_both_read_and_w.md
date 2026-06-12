---
title: "what file system can mac and linux both read and write to?"
date: 2011-08-13
forum: Apple Hardware Users
---

### Post by jewfromdahood on 2011-08-13
Hi I am buying a macbook pro 17" soon, as now they have almost everything I want in a laptop so I don't have to lug around the heavy 17" one I built two years ago. They have an AMD GPU, but Intel CPU. and are great in general as they dont use winblows. My current laptop uses Ubuntu 11.04 amd64. So I will be putting Ubuntu 11.04 amd64 on the macbook pro once I install a new seagate 750GB 7,200RPM HD. And two of the reasons I am getting a mac is 1) it's not winblows, and 2) I know it will work great with my iPhone and iPad. I also have a MacBook air that was given as a gift but I hate it and doesn't have enough space plus no dvd drive. I am wondering what file system can Linux and Mac both fully read and write to as I will be switching between the two. Mainly will use Linux. Mac will only be for iTunes, and video editing. As Mac OS X still doesn't seem as fast as Linux in my view. Nor as customizable. But it does have a couple apps that are really cool that Linux doesn't quite have. But the Linux laptop I built can have two GPU's and HD's. Not too shabby. 
I need to know as I want to store my music and videos on a filesystem that can both read and write to a partition on both linux and mac.
I don't care if it means installing a driver or whatever on Mac as long as it works, and works well. And no I don't want it on Fat32. As I may be storing some files bigger than it allows. Thanks for taking the time to read this and help out guys!

---

### Post by pindar on 2011-08-13
Well, if you don't want FAT, I think your best bet is hfsplus unjournaled. Both OS X and linux can read and write. I have found it to be reliable, but I've never done I/O intensive things like video editing, so YMMV.

pindar

---

### Post by johnmurrayvi on 2011-08-13
If you disable journaling on the HFS+ (Mac) partition, you can have R/W ability from Linux. If you just want to listen to your music and watch your videos, but not be able to update the files, e.g. a song's metadata or playcount, you can leave journaling on and the HFS+ partition can be used as a R/O volume.
I have 11.04 x86_64 and Snow Leopard on my iMac and have all of my music on my Mac partition but simply mount it R/O and imported (but didn't copy the files) into Banshee and can play all of my music without any issues.

---

### Post by jewfromdahood on 2011-08-13
I'm thinking of having three partitions. Mac OS X, Ubuntu, and the third party partition. Third party partition will mainly have my 90GB+ of music, plus some space for movies. Or knowing how many movies I store I will probably have it on flash drives and externals when I watch them.

---

### Post by johnmurrayvi on 2011-08-13
> **jewfromdahood said:**
> I'm thinking of having three partitions. Mac OS X, Ubuntu, and the third party partition. Third party partition will mainly have my 90GB+ of music, plus some space for movies. Or knowing how many movies I store I will probably have it on flash drives and externals when I watch them.

Coincidentally, that's how I have my MacbookPro setup... my partions: [ESP | Mac | Ubuntu | Media] I have to say that set up also works well. I believe the Media partition is formatted to Ext3 (I'll double check but I'm not on it right now) and I have Fuse-Ext2 installed on OS X.

---

### Post by jewfromdahood on 2011-08-13
Regardless in my view the pecking order is Linux > Mac OS X > Winblows
I wish apple would make iPhone work completely in an iTunes for Linux! Then I would really have no need for anything but Linux!
Linux is starting to gain popularity in the mainstream too. I am in the process of make an HP Proliant DL180 G6 server as a dual wan gateway/firewall/dns-cache/anti-virus server all in one for a company I love Linux. Especially Ubuntu.

---

### Post by crook17 on 2011-08-14
this may help a tad.
[http://en.wikipedia.org/wiki/Comparison_of_file_systems#Supporting_operating_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Supporting_operating_systems)

---

