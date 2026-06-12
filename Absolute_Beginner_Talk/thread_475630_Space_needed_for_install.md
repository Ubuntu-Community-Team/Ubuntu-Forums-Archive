---
title: "Space needed for install"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by OPle on 2007-06-16
I Wounder how big partition i would need for installing and using Ubuntu with normal functionality?

---

### Post by hoges on 2007-06-16
This question is kind of ambiguous. It all depends on the software you install, files you keep on it, etc.

I've installed it on a 15gb hdd no worries, but you may want more if you keep everything on the same partition.

Also, keep in mind that linux doesn't properly support writing to ntfs file systems (ie the xp one), and by default xp can't see the linux partitions - worth noting if you're dual booting.

---

### Post by OPle on 2007-06-16
Had planed to make a dual boot setup, have a 80gb hard drive 10gb used for the windows partition, and the rest is at the moment used for a entertainment partition, how much would you recommend using on the Ubuntu partition (just for the os and the applications)? Had planed to resize the entertainment partition and make a linux  partition, would work?

---

### Post by starcraft.man on 2007-06-16
> **OPle said:**
> Had planed to make a dual boot setup, have a 80gb hard drive 10gb used for the windows partition, and the rest is at the moment used for a entertainment partition, how much would you recommend using on the Ubuntu partition (just for the os and the applications)? Had planed to resize the entertainment partition and make a linux  partition, would work?

The absolute minimum for an Ubuntu partition to fit from a clean install is I think 4GB. I recommend between 6-8 GB to allow Buffer for installing applications, other window managers and other large programs. A 1 GB swap should do you fine as well, if you have lots of ram, 3 GB or more, reduce it to 256 MB, you don't need it much when you get to really huge amounts of actual ram.

And yes, you can resize the partition in question without any trouble. If you don't have a partition editor, use Gparted live CD (google it).

---

### Post by OPle on 2007-06-16
Thanks, will give it a try:p

---

