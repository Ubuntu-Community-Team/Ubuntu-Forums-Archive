---
title: "How to GPartition"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-04-12
I presently have a dual boot system with Dapper and XP.  Now I want to remove Dapper and use that partition (the larger one) to install Edgy on.  My problem is I'm unsure how to use Gparted to achieve this.  

I'm presently in the install process where I have selected to manualy partition and the screenshot hopefully shows what I have on my system at the moment.  Can someone help me to sort this partition business out please as I am desparate not to loose the websites I have in Frontpage which are in my XP partition.

Xp is in the smaller partition I beleive?

[ATTACH]29570[/ATTACH]

---

### Post by vatechtigger on 2007-04-12
XP is the partition labeled NTFS. EXT3 is your Linux partition.

---

### Post by steve.horsley on 2007-04-12
I can't offer screenshots, but I believe that if you select guided partitioning, you can actually choose simply to reformat /dev/hda2 and change the mount point from /media/hda2 to /. 

Please, please backup your data first. Just in case of something going wrong, or a fire, meteorite strike etc.

---

### Post by a.v.l on 2007-04-12
> **vatechtigger said:**
> XP is the partition labeled NTFS. EXT3 is your Linux partition.

Thanks for that, can I ask for some instructions on how to install Edgy on the Dapper partition, I've not done this before.

---

### Post by Dual Cortex on 2007-04-12
Maybe it's because you don't have a broadband connection, etc., but just *in case* you didn't know, you can also **upgrade **Dapper to Edgy.
See 
[http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html](http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html) for a simply How-To

---

### Post by a.v.l on 2007-04-12
Having kept the same partitions during the edgy install I have been able to install Edgy on what was the Dapper partition and also kept my XP partition too.

I now wish to change the size of both partions so that my Ubuntu Edgy partition is the larger of the two.  How can I do this please?

---

