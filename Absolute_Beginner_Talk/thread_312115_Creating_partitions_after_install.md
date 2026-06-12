---
title: "Creating partitions after install"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by Hex_Mandos on 2006-12-03
I installed Kubuntu yesterday. I've just had some minor annoyances, which I hope to correct soon. However, I need to make my system dual boot. I know most people recommend installing Windows before Ubuntu, but my Windows CD didn't want to cooperate: it wouldn't recognize the partitions it itself created as windows partitions.

How do I format and partition a blank hdd after installing? I can't find a partitioning/formatting tool either in KDE or Gnome. I want to create something Windows can install itself on (preferrably NTFS, but I'm frustrated enough to just get it done in FAT)

To think people (including myself until now) consider Linux hard to install...

---

### Post by Bartender on 2006-12-03
Download [GParted]("http://gparted.sourceforge.net/livecd.php") LiveCD.

Burn the download to a CD.  If done right, it'll boot up like an UbuntuLiveCD.  Wipe out all partitions, create a primary partition in the front of the disk (to the left in the disk map) and format it as NTFS.  Make another primary to the right of the Windows partition, format it as ext3.
Toss in your Windows CD, make sure it installs to the NTFS partition.  Check it out, make sure Windows works.  Toss in your Ubuntu CD, follow aysiu's LiveCD directions.

---

