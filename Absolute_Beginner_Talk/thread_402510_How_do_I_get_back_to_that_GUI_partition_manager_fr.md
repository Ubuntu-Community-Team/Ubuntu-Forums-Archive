---
title: "How do I get back to that GUI partition manager from when I installed Unbunu?"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by SlaughterDog on 2007-04-05
I am new to Linux and Ubuntu. When I installed Ubuntu from a live CD, I got a nice GUI partition manager to set up my partitions for installation. I do not know how to use the command line and would like to get that GUI partition manager back, but can't find it. 
Also, during installation I chose not to mount my NTFS partition, however now I'm wishing I had! Does that GUI partition manager make it easy to mount partitions, or can someone show me how to do so useing the *cringe* command line?

---

### Post by luckyd on 2007-04-05
Go to synaptic and download gparted. This will give you gui partitioning, however I don't think that it comes with the ability to mount NTFS filesystems. (I being a noobie myself am not sure)
apart from that Gparted will solve most partitioning needs \\:D/

---

### Post by ramjet_1953 on 2007-04-05
Firstly, you can't re-partition a drive which is active.

But don't despair, there are a few of ways to attack your needs.

1. Go to this site [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) and download the Gparted Live CD and then burn it to a CD as an **iso** file. It must be burnt as an iso and burn it SLOWLY - no faster that 4X on high quality media. It fits nicely onto one of those half-size CD's.

2.Go to this site [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) and also download the iso image and burn it. This package offers a lot more features.

3. You can also use your Ubuntu Live CD and use GParted from there.

In conclusion, remember to back-up your home partition first. That way if you do mange to hose your system, it is much easier to set it back up.

Regards,
Roger :cool:

---

### Post by BoJon on 2007-04-05
In following this thread, if you have XP and Ubuntu on the disk with dual boot, can you use a Win program like Partition Magic or Disk Director to partition or change partition in the Ubuntu part?

---

