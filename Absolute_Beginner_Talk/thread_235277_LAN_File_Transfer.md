---
title: "LAN File Transfer"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by camRW on 2006-08-12
I plan on doing my first Ubuntu dual-boot installation today.  I've installed Ubuntu previously and I very little experience with partitions.  I have 74 gigabytes of space on my hard-drive and only 37 GB of free space.  What would be the best way to partition my hard drive?  And should I have to worry about backing up my files (by LAN) when doing this?

---

### Post by gerbman on 2006-08-13
Read [this]("http://www.psychocats.net/ubuntu/partitioning.html"), [this]("http://www.psychocats.net/ubuntu/installing.html"), and [this]("http://www.psychocats.net/ubuntu/separatehome.html") first. It's a lot of information, but it's all relevant and important. Backing up files before messing with partitions is always a good idea. Post any questions you might have.

---

### Post by camRW on 2006-08-13
I've already read those before, and maybe I fail at reading comprehension, but I still can't figure out which one is best for me.  I'm starting to backup everything right now.

---

### Post by gerbman on 2006-08-13
> **camRW said:**
> I've already read those before, and maybe I fail at reading comprehension, but I still can't figure out which one is best for me.  I'm starting to backup everything right now.I would go with the partitioning scheme in the picture I've attached. It's nice to split the Ubuntu partition into a /home and root (/) partition because if you ever want to reinstall Ubuntu you can just reinstall over the root (/) partition and reuse your /home partition, saving all of your home directories and their preferences, settings, etc.

The easiest way to arrive at this installation is to install Windows first, leaving half of the drive for Ubuntu. You'll need to create three partitions in the free half of the drive during Ubuntu install:  home, root (/), and swap. I would use 1GB for swap, 2/3 of the remaining for home, and 1/3 of the remaining for the root (/) partition. To do this, use the "Manually edit partition table" option during the installation. Remember which partition numbers (hda1, hda2, etc) belong to which partition (home, root, swap). In the "Prepare mount points" window (following the partition creator), make sure to mount the root partition number (say, hda1) at the mount point "/", the home partition (say, hda2) at "/home", and the swap partition (say, hda3) at "swap". In addition you can mount your Windows partition at a location like "/media/Windows", but MAKE SURE to uncheck the box that says "Reformat", or else you'll lose your Windows installation.

---

