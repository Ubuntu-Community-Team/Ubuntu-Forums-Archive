---
title: "Dual Booting Windows/Ubuntu on Acer laptop"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by Xitanto on 2006-03-20
I have an acer aspire 3600 laptop (which, btw, I love) that has one 60gb drive. When I recieved it, it was already partitioned twice.

Since then I've split the second partition (ACERDATA D: ) into two - ACERDATA D: and Ubuntu G:

So I have:

ACER C: FAT32 28gb
ACERDATA D: FAT32 ??gb (who cares)
Ubuntu G: NTFS 5.2gb

When installing Ubuntu BB 5.10 the only options I am given are to reformat the entire drive. Or at least that's what I think anyway. It's all chinoise for me.

Someone please help me here! I want to dual boot between Windows XP and Ubuntu. I'd also like to know how easy/hard it is to remove Ubuntu if I ever want to play around with other distros as well. :)

PS. Quite obviously I want to select the drive I've labelled Ubuntu for the installation.

---

### Post by AtinLango on 2006-03-20
At the partitioning stage, choose manual (I think the last option). And you will have to change Ubuntu Partition from NTFS to ext3 or I think also reiserfs. I am using ext3.

For unistalling, you can make a new installation over Ubuntu whenever you wish.

---

### Post by Sef on 2006-03-20
If you want to share files between XP and Ubuntu, then you need to set up a ext 2 partition.  Otherwise ext3 or reiserfs will work fine.

For info on dual booting, here is an excellent tutorial:  [http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by dermotti on 2006-03-20
Windows XP can read/write to ext2?

---

### Post by Xitanto on 2006-03-20
Good news - I now have my first working dual-booting system. And it works too!

All I need now is to get my wireless card running.

---

