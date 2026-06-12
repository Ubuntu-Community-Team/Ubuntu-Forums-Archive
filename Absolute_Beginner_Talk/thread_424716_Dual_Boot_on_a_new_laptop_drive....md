---
title: "Dual Boot on a new laptop drive..."
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by Sporkmaster on 2007-04-26
At the moment, I have a 

**20gb hard drive patitioned:**
 15gb Windows XP
 5gb Windows Recovery Partition (Same thing as on the CDs)
**2gb flash drive partitioned:**
 1.9gb Xubuntu
 100mb Swap
[B]60gb hard drive unpartitioned
IBM Factory default reset CD's, including Windows XP install
Xubuntu Edgy CDs - both normal and alternate[/B]

I now want to partition this NEW drive with 30gb Win-xp, 30gb Lin-x

However, I cannot have both hard drives plugged in at the same time, and partitioning destroys all data on the disk

Does anyone know how to do this?

---

### Post by LaRoza on 2007-04-27
You can resize the partition and then add a new one in the space created.

When altering partitions, there is always a risk data will be lost, so backup.

---

### Post by dstew on 2007-04-27
The best partitioning tool is GParted. I don't know if it is on the Xubuntu 7.04 Live CD. If so, you can install the new drive, but boot the Live CD, then partition the drive using GParted.  If Xubuntu does not have GParted, you can make a GParted Live CD (see [http://gparted.sourceforge.net/livecd.php)](http://gparted.sourceforge.net/livecd.php)), boot from that, and partition your new disk.

---

### Post by Sporkmaster on 2007-04-28
Ok... I'm not going to back it up because for all intensive purposes it's a new computer. If I partition Windows' area first, leaving the rest unpartitioned, then I can partition Xubuntu when I install it?

---

### Post by dstew on 2007-04-30
If you want to end up with Windows XP and Xubuntu on the new 60 gb drive, the most straight forward way to do it is to install XP first using your XP install disk, and let it have the whole disk. Then, install Xubuntu, and during the intallation process tell the partitioner to shrink the XP partition down to 30 Gb. Install Xubuntu into the freed-up 30 Gb.

---

