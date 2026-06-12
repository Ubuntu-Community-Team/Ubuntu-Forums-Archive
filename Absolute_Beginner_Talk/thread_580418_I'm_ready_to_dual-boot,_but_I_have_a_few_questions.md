---
title: "I'm ready to dual-boot, but I have a few questions first..."
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by nabl on 2007-10-18
Now, before I start I'd like to mention that I know most of these questions have been asked before, but I still haven't found definitive answers, even after reading through A LOT of similar topics. Sorry for making you answer the same questions over and over again... ;)

The main problem here is partitioning for me. I'm currently running XP, and I have been using Kubuntu (I prefer KDE to Gnome) for a few months now. I had previously installed Ubuntu with wubi and simply added the KDE components to Ubuntu. Now, with the release of Gutsy Gibbon (which I've been waiting for excitedly), I would like to have an actual dual-boot system.

I have a 500 GB hard-drive with 2 partitions with about 30 GB for Windows/programs (C: ) and 440 GB for music, videos, games, etc. (D: ). The rest was lost when formatting the drive. What I would like to do is separate the 440 GB partition into a 415 GB partition (for Windows files, etc. still), 2 GB for swap, and the remaining 23 or so for Kubuntu. I am very concerned about losing data in the process of doing this, however, so I want a definitive answer before starting. I do have important data backed up in case something would happen, but it would be quite a hassle to start over from scratch.

I have successfully fragmented both partitions multiple times, like I read in various other threads, so I have that out of the way. So, where do I go from here? Is there a way to do what I want with the partition manager on the Live CD installer?

I guess what I'm asking in all of this is for step-by-step instructions on making these partitions. The main reason I'm asking is because I haven't found a situation in which someone else already had two Windows partitions and wanted to break them down farther. (I hope I'm making sense... :()

I thank you all in advance for your help, and I look forward to posting here more often--hopefully helping more than asking for help. :razz: I also look forward to having a "real" Kubuntu installation. :)

---

### Post by Duck2006 on 2007-10-18
You can do the install and partitioning from the live CD

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by p_quarles on 2007-10-18
Definitely read the tutorial that Duck2006 posted. It's written by one of this forum's most active members, and is absolutely accurate. 

That said, what you're doing is really straightforward. You've already defragged the drive, you have backups of crucial data, and you have the installation disk. All you really need to do is boot the disk, select "install" from the desktop, and when you get to the partition editing menu, select "automatically resize and install on newly freed space." Shrink the data partition by 25 gigs, and the program will automatically create the appropriate root and swap filesystems. 

I understand some people have had minor issues with getting the new release to properly read NTFS partitions. If you have any problems with that, of course, stop by and ask. Good luck. :)

---

