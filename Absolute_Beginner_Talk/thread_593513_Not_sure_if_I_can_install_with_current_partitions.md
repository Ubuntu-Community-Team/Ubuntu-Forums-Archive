---
title: "Not sure if I can install with current partitions"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by nickyspaghetti on 2007-10-27
I don't know if I will be able to install ubuntu using my current partitions. I have two hard drives, both split into two. On my master I have windows, and the other part is storage, both ntfs. The other is a large storage drive and a 9 gig partition I set aside for ubuntu. These are also ntfs.
Will ubuntu be able to read and write to these drives. I don't want to lose any info on them by accident. Do I need to find a way to reformat?
Also will ubuntu run from the slave partition?
Thanks in advance.
Nick

---

### Post by proalan on 2007-10-27
A true linux installation requires you to reformat one of your drives. 
You will need the ntfs-tool to read and write onto ntfs partitions from ubuntu.

There exists an alternative install that preserves your ntfs partitions without modifying anything.

[http://wubi-installer.org/](http://wubi-installer.org/)

Just to note, if your going to install with wubi there is a 10GB size limit with the virtual disk.

---

### Post by nick_h on 2007-10-27
Let Ubuntu reformat the partition you are going to install it to.  You probably will also want to create a small partition to use for swap.

The ntfs-3g package in Ubuntu will let you read and write to ntfs partitions.

Remember to backup your data first just in case.

---

### Post by sneezymelon on 2007-10-27
Use Wubi. It's nice and simple and will simply create a virtual drive on your existing hard drive instead of the partition with no need of reformat

---

