---
title: "Dual Boot Help"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by perito on 2008-04-09
I currently have Windows XP SP2 and Kubutnu 7.04 (Fiesty) installed on my system. After the new version of kubuntu is going to be available (Hardy), I want to remove my old kubuntu and install a fresh new Kubuntu...
My question is, how do I remove the old Kubuntu without damaging windows?
thx

---

### Post by bumanie on 2008-04-09
You don't have to uninstall your old kubuntu. At the partitioning stage just ensure you get hardy to install to the same partitions that feisty is now on. The partitioner formats the partitions it is going to write to - so goodbye feisty. Hardy will install a new grub so that won't be a problem either. What you may have to do to ensure hardy writes to the correct partitions is to choose manual at the partitioning stage.

---

### Post by StRiFe10101 on 2008-04-09
I'm not an expert but if the bual boot was done properly you should have two different partitions.  One with linx and one with windows. Use a utility like, gparted, to simply format the partition or destroy and recreate the partition.  then you can install it like you did before with the later version of kubuntu.

---

