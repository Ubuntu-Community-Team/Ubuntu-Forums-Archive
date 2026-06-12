---
title: "Quick partition question"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by jonsayer on 2007-02-22
I just have a quick, final partitioning question.

I read in this [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) installation tutorial how to partition my hard drive when I install Ubuntu with gparted. It seems simple enough. But i do have a question...

[http://img130.imageshack.us/img130/2201/w2u31c3ij.png](http://img130.imageshack.us/img130/2201/w2u31c3ij.png)

check out this image. When i get to this stage of partitioning, when I enter "/windows" into one of the mount points, as shown in the picture, that will put all my current windows files and installation into that partition?

---

### Post by mikewhatever on 2007-02-22
Yes and no. /windows will be more like a door to all your Windows files. Check out the screenshot of mine.

---

### Post by jonsayer on 2007-02-22
so how do I preserve my current Windows install in one partition? do I just make a new partition, and the old partition and everything in it will work fine?

---

### Post by mikewhatever on 2007-02-22
Windows and Ubuntu live on separate partitions with different file systems. By installing Ubuntu, you do not delete or move Windows or Windows partition. It stays were it was. You may need to resize it to free some space for Ubuntu, and then create Ubuntu partitions in that space. Mounting Windows into a folder does not move it to that folder, but just gives you access to the files through that same folder.

---

