---
title: "Trustworthy Partition Imagers safe for Linux?"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by getut on 2007-10-29
I am well into my first foray into using Linux in a server environment. I am using Ubuntu Gutsy server as host to some virtualized Windows machines.

I have a massive Dell 2900 w/ 32GB of RAM and 8 750GB drives and am having the performance issues talked about in this thread [https://answers.launchpad.net/ubuntu/+question/4107]("https://answers.launchpad.net/ubuntu/+question/4107")

I want to try one of the fixes listed which is to use a stripe size on the raid of 256k. I will need to set up the RAID volume from scratch to do this, but I dont want to have to reinstall and setup everything again.

Is g4l (ghost for linux) safe for imaging the partition, recreate the raid volume, and restore the image of the partition? If not, any other programs? Can I use them from the Ubuntu live CD?

Please help.

---

### Post by julian67 on 2007-10-29
[Clonezilla]("http://clonezilla.sourceforge.net/") and [Clonezilla Live]("http://clonezilla.sourceforge.net/clonezilla-live/") are well worth looking at. I use Clonezilla Live CD regularly for disk imaging and I don't recall ever having a problem except the classic "I cloned my blank disk to my working disk! Oh sh..sh..shame!"

The core program is partimage but Clonezilla adds a lot of nice features and capability. Partimage is good in itself, you can find it on a lot of rescue CDs. As I recall g4l relies on dd so copies all disk sectors whereas partimage only copies used sectors and is likely to be considerably quicker to use unless your disks are close to full.

---

### Post by steve.horsley on 2007-10-29
I have used tar from a live CD to save and later restore a LInux system (I saved the tar file on an external USB drive).

---

