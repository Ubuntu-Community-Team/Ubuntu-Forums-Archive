---
title: "Questions about partitioning"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Skneepa on 2007-06-15
Hi, it's the first time I'm installing a linux distribution so I have to stick with dual boot until I get familiar with Ubuntu. My question regards partitioning...I have an 160GB SATA HDD, split into three partitions (one for XP, one for games and applications and one for general storage). What I want to do is to install Ubuntu on the last "storage" partition which is about 50Gbytes. It is currently formated in NTFS. Can I just delete the partition using windows disk manager and reformat it whith Ubuntu installer? I do not want the operating systems to interfere with each other, that's why I want to go this way. At this moment I do not need to share files between the operating systems. Will Ubuntu installer detect the unallocated space without changing anything in the NTFS volumes? It is important for me to do so as a lot of work being developed is stored in the NTFS volume.

---

### Post by FleetAdmiral74 on 2007-06-15
When you install ubuntu, you can choose to delete the data partition you mentioned, and then format it, it will take care of it. It should auto-detect the xp partition and set up the dual-boot for you as well. Just make sure you have backed up your data on the partition you are deleting, it will go byby. Oh, and unless something really weird happens, it should not affect your other partitions.

---

### Post by scrooge_74 on 2007-06-15
You can let the Live CD do all the work, it comes with a program call ed Gparted, it will let you resize the disk and then you can format that space into ext3 so you can install Ubuntu on it.

---

### Post by Kobalt on 2007-06-15
The Ubuntu LiveCD comes with a partition tool, which is launched during the install process. When it will come up, select the third partition, on which you want to install Ubuntu, and it will be formatted automatically. Without touching the two other. 
If you need more help on partitioning, [read this]("http://psychocats.net/ubuntu/partitioning").

Welcome to Ubuntu :) !

---

### Post by Skneepa on 2007-06-15
Thanks a lot people - all of you! Never had seen such a quick response in a forum before! And that's why I'm gonna stick with Linux even if Windows get a plugin that makes your coffee for you and stuff! Because the whole DIY thing and the community of Ubuntu are really great! I'll try installing Ubuntu as soon as I get home!

---

### Post by byen on 2007-06-15
Yup! the posts made pretty much explain how simple the process is.An advise. If you decide to resize your storage partition instead of formatting it (the whole) ... Please defrag your partition before you resize it. It is not a must, but  advised. Good luck! Let us know if you run into trouble.

---

