---
title: "What should be the size of root drive ?"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by dptxp on 2007-03-08
I am new to Linux, installed the 64-bit Ubuntu 6.10 last week. I have kept 4 GB for root drive. How large should it be ? Can programs be installed in other drives too ? If yes, then should they be ?

---

### Post by Kateikyoushi on 2007-03-08
I would rather recommend a bigger partition for the root especially if you are new to linux because you might want to try different desktop environments as then 4GB is not enough for kde and gnome. It would be easier and more adviseable to resize the partition than to try to install software on other partitions.

---

### Post by waldschm on 2007-03-08
For more on the topic see [this page]("http://www.psychocats.net/ubuntu/partitioning") written by an experienced ubuntu user. The size of your root partition will depend on the way you setup your partitions and could take into consideration factors such as whether or not you're dual booting windows. Just for reference, I'm currently using up about 4 GB for my root partition although I gave it 14 GB on my laptop.

---

### Post by guitarist549 on 2007-03-08
I generally set mine to about 9 gb... I usually have 2-4 gbs spare at any given time on my root partition.
Do you guys see any benefit to having different partitions for each folder?
i.e. boot, usr, var...

---

### Post by Patrick K on 2007-03-08
4gb is going to be tight. I'm at 4gb used right now after 2 months. And not all that many apps installed. A few weeks ago I expanded / to 13gb and made a separate /home partition. / is filling up much faster than /home so far. AFAIK, you cannot choose which partition or directory to install programs. The way the Linux file system works makes it difficult at best. 

With Windows I would install certain apps in certain partitions or directories. I don't think you can do this with Linux. I think the best you can do is set some of the directories to different partitions. I haven't looked into this, myself. But the apps will still install in the directories Linux wants them in.

---

### Post by Kateikyoushi on 2007-03-08
> **guitarist549 said:**
> I generally set mine to about 9 gb... I usually have 2-4 gbs spare at any given time on my root partition.
Do you guys see any benefit to having different partitions for each folder?
i.e. boot, usr, var...

I don't really see benefit from that, people did it on the gentoo forums but with different filesystems to achieve better performance, with the little differences between filesystems I am quite sure it took longer to configure the system than they could benefit.

I am around 4-5 GB with just gnome with KDE and Xubuntu around 7.

---

### Post by dptxp on 2007-03-08
Thanks. I have been through the psycocats page as suggested, in fact made sure that I did proper job the first time. My laptop has a 60 GB HDD, has widows-xp, had D and E drives, 20 GB each. I kept D drive for data, partitioned E drive - 4+ GB for '/', 4 GB for swap and rest for data (FAT32).
Now I guess I shall change it to 8192 MB for root, 2048 MB for swap and rest FAT32.
BTW, QParted, installed later, gave me problems when I tried to correct the mounting of the 10+ GB FAT32 drive. I instead put on the Installation CD in LIVE mode, used GParted, noticed that I had entered hds/ inplace of hda/, used info at [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
to correct it. And all was fine. I am finally getting used to Linux Terminal.
I plan to stick to the 64-bit version. That is the way it can grow.

---

### Post by waldschm on 2007-03-08
> I don't really see benefit from that, people did it on the gentoo forums but with different filesystems to achieve better performance, with the little differences between filesystems I am quite sure it took longer to configure the system than they could benefit.


Although probably not that common among ubuntu desktop users, there are benefits to having different partitions for /tmp /boot /opt  etc... The primary benefits are disaster recovery and enhanced security. Wikipedia has a little on the subject [here]("http://en.wikipedia.org/wiki/Disk_partitioning") under the Partitioning Schemes section. [This website]("http://www.cyberciti.biz/tips/the-importance-of-linux-partitions.html") has a more in depth explanation of attacks against improperly partitioned systems.

---

