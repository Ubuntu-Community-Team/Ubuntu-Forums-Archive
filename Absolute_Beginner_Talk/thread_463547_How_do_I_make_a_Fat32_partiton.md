---
title: "How do I make a Fat32 partiton?"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Romanus81 on 2007-06-03
I recently downloaded Wubi, and in the future I might go for partitioning my hard drive, but I heard that it would cause the data on my hard drive to be deleted, so until I can get a way to backup all my data, I decided to stick with Wubi.
To share firefox and thunderbird information between windows and ubuntu, I need a Fat32 partition, right? How do I make that, and will making it cause all the data on my hard drive to be lost?

---

### Post by oilchangeguy on 2007-06-03
> **Romanus81 said:**
> I recently downloaded Wubi, and in the future I might go for partitioning my hard drive, but I heard that it would cause the data on my hard drive to be deleted, so until I can get a way to backup all my data, I decided to stick with Wubi.
To share firefox and thunderbird information between windows and ubuntu, I need a Fat32 partition, right? How do I make that, and will making it cause all the data on my hard drive to be lost?

the only way your data will be deleted, is if you partition wrong when you install ubuntu. otherwise there should be no problem. of course it's always wise to backup your data anyway, what happens if your hard drive dies?

---

### Post by antoz on 2007-06-03
You can create your partitions with Gparted it comes with the live Ubuntu CD. A couple of good links.
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by louieb on 2007-06-03
How to make a partition? 
1st you need space on your disk that is not already in a partition. 
This can be done by[LIST]
[*]deleting an existing partition
[*]shrinking an existing partition[/LIST]Obviously if you delete a partition all the data is deleted too. Shrinking a partition can be done safely but before you do. If its a windows formated partition[LIST]
[*]defrag the partition
[*]defrag the partition again
[*][A better windows defragmenter.]("http://kessels.com/JkDefrag/index.html")
[*]run scandisk
[*]backup you data (unless you feel lucky)[/LIST]Once your ready to create the new partition: Partition Magic or [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") is a tool you can use. [GParted Documentation - general.]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

[Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

---

