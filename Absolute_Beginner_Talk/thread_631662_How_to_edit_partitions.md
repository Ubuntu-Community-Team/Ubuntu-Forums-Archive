---
title: "How to edit partitions"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by -gabe-noob- on 2007-12-04
so I have this windows partition that takes up half my drive and I never use it, Is there any way a noob can make it go away, preferably in a fire(lol)

---

### Post by -gabe-noob- on 2007-12-04
How come no one ever awnsers my posts? _bump_

---

### Post by Paqman on 2007-12-04
You could just reformat the partition with Gparted and use it as general storage. To merge it with your current partitions would mean having to back up all your Ubuntu data (just in case), which seems like a hassle to me. 

If you did want to, again, Gparted will sort you out. Just delete the partition and grow the others to fill the space. You can't make changes to any partition which is mounted though. Luckily there's a [LiveCD version of Gparted](http://gparted-livecd.tuxfamily.org/) that you can boot into and grow these partitions with.

---

### Post by overdrank on 2007-12-04
> **-gabe-noob- said:**
> How come no one ever awnsers my posts? _bump_

Well I would wait more that 8 mins. But you can use gparted on the live cd and delete the partition and create or resize your ubuntu partition.

---

