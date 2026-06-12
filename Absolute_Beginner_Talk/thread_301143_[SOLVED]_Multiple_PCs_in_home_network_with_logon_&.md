---
title: "[SOLVED] Multiple PCs in home network with logon &amp;amp; prefs keep on 1 PC.Server setup ne"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by minutest on 2006-11-16
I am very new to Linux but after looking at the live CD ubuntu looks like a very powerfull OS with out being Over bolted like some other OS's.
My ? has multi tiers. 1st some info. I have 3 PC's & working on building my 4th PC now. None of them have ubuntu installed on a  hard disk yet.
When all PC's have ubuntu on there HD will I be able to setup network so that 1 PC holds all info for log on including preferences/email etc...Will this PC need to be setup as a server?
I have 4 kids and our pier-2-pier network (some settings save on pc1 others on pc2 and others on pc3 has gotten out of control). I am looking to be able to log onto any pc and have settings the same. 
Hope that some of this makes some since. Sort of a weak ? but b4 I make a big leap into new OS I am going to ask some bad/dumb ?'s.
Thx.

---

### Post by echo $USER on 2006-11-16
What you need is NFS (network file system)...

[http://nfs.sourceforge.net/nfs-howto/](http://nfs.sourceforge.net/nfs-howto/)

You can have everyone's /home/user directory on the master server and mount it on other clients once they log in to that particular client.

---

