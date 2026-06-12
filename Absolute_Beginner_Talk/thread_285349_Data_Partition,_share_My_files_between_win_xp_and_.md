---
title: "Data Partition, share My files between win xp and ubuntu"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by Jamesbowden on 2006-10-26
I have had Ubuntu on my laptop for a little while now and have enjoyed it.

Now i want to put it on my new family computer. the problem is the rest of my family don't to use Ubuntu Linux, they want to stick with windows.

So i thought what i is split my drive into Three partitions. 
1- the Windows Xp operating system and programs
2- Ubuntu operating system and programs
3- Data (Music, video, office documents, ect.)

I have an 80gb hard drive. 

i have asked my family what programs they would want to use on windows, and it is about 5gigs worth.

all to geather they have 31 gigs of data in their "my documents"
 
i have a few questions about this. firstly what format  should i make the data drive so that both Windows and Linux can read it?

how much space should i give each partition?

---

### Post by Brownedwg89 on 2006-10-26
make the data partition a fat32 partition, since linux and windows both can read/write to it

---

### Post by meng on 2006-10-26
Unless you have loads of programs to install for Ubuntu, you shouldn't need more than 10 GB for / (root) and that's being very generous indeed. I'm not sure how much Windows demands these days. Give the rest to your data partition, format it ext3 and install FS-Drive on Windows.
[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning). Remember to have a Linux swap partition also.

---

### Post by dbott67 on 2006-10-26
I would create a 15 GB Windows partition, 15 GB for Ubuntu & the rest (50 GB) would be a FAT32 partition for data.

---

### Post by Jamesbowden on 2006-10-26
Thanks Guys,

Im gunna try the FS-Drive thing, and if i have problems with that ill go for the fat32 option

---

