---
title: "Partition resize woes"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by bytecrawler on 2007-07-28
I'm trying to resize an ext3 partition (not the root partition) using GParted and I'm running into what seems to me to be a pretty goofy problem. Whenever I try to unmount the partition, it immediately remounts. the GParted display doesn't see this immediately and I can attempt to resize, but the operation will fail at fsck because the partition is mounted. I'm not sure if GParted is automatically remounting or if some other process is doing it, but I can't find any way to stop this behavior. Considering I'm getting the same behavior even when I boot from the CD, it doesn't seem to be anything I've done to my configuration. I've found a bunch of threads talking about resize issues, but no one has mentioned this one which is telling me I'm probably missing something pretty obvious. Any ideas?

---

### Post by cotcot on 2007-07-28
You run GParted from the Ubuntu liveCD ?
Better download and burn the GPartedLiveCD. Boot from this CD and resize the partition. You will not have the automount in the GpartedLiveCD.  (I have had the same issue some time ago and you this CD ever since)

---

### Post by ReaderRat on 2007-07-28
[**Gnome PARTition EDitor = gparted**](http://gparted.sourceforge.net/index.php)

---

### Post by bytecrawler on 2007-07-29
Thanks, I will definitely look into the GpartedLiveCD. A friend did point me to a way around the problem and it was just as simple as I thought it might be. In the System/Preferences menu, there is a utility for settings related to "Removable Drives and Media." All I needed to do was uncheck "Mount removable drives when hot plugged" and "Mount removable media when inserted." Apparently Gnome can't tell the difference between an unmounted internal partition and unmounted external drives/media.

---

