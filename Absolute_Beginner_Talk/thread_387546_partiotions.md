---
title: "partiotions"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by ceezax on 2007-03-18
hi there

i just have my new hard disk and i installed ubuntu with the default settings for 

auto partitioning and i have this configuration 

 Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9648    77497528+  83  Linux
/dev/hdc2            9649        9729      650632+   5  Extended
/dev/hdc5            9649        9729      650601   82  Linux swap / Solaris


so i just need to partition my free space into 3 partions , so how can i do that ?? 

but i just want to make sure that i will have no changes for the current configurations 

i just need to partition this free space and mount them as partitions in my home

---

### Post by AtrejuT on 2007-03-18
I don't really see any free space - yet. But that's easy to get:
You'll have to boot either a Ubuntu LiveCD or a gparted liveCD to change your root partition. If you do that and start gparted you can resize you root partition (hdc1) to create free space, then create a new primary partition in the space you freed up that way.

---

### Post by barney_1 on 2007-03-18
Here's some gparted docs if you need a hand:

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

