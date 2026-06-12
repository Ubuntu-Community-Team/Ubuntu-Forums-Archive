---
title: "help with dual booting XP and ubuntu"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by newyawker on 2007-03-14
hey

I've been using XP and I decided I want to dual boot with ubuntu.  I downloaded the iso, burned it to disk, and popped it in.  I found some guides online on how to resize my xp partition.  I resized it, which works, and I also made a swap partition and another partition for ubuntu.  

The ubuntu installer says I need a partition on the root "/" , however, If I try to put a partition on "/" It says the root partition doesn't exist.  So right now, I have the XP partition, the swap partition, and the ubuntu partition on my disk.  However, I also have a tiny partition about 70MB in size at the very front of my disk.  It came with my computer (dell lattitude d610).  Is it ok if I erase this tiny partition, because I think I may need to use the 4th partition as a root partition or something.  Any ideas on how to make this work?

Thanks

---

### Post by deathbyswiftwind on 2007-03-14
Hey I wouldnt erase that partition. Alot of times that tiny partition has files needed by your restore disk. What I would do is rerun the partitioner, delete all your linux partitions and then have it use free space and it will auto partition it for you.

---

### Post by raidlost on 2007-03-14
**[SIZE="3"][COLOR="Red"]DON'T[/COLOR][/SIZE]**

---

### Post by newyawker on 2007-03-14
Should I also erase the swap partition?  Or will that also be automatically set up too?

---

### Post by raidlost on 2007-03-14
the tiny partition on the front is the recovery partition

---

### Post by deathbyswiftwind on 2007-03-14
Yes go ahead and erase the swap partition. When you select it to use free space it will create your root partition (/)  and your swap partitions.

---

### Post by raidlost on 2007-03-14
best bet 

boot with a OS that allows you to use a tool such as LINUX fdisk or partition magic

the partition that has been set aside for the / must be set to ext2/ext3 and if you are in linux use mkfs to (format)

or

during the installation of ubuntu manually edit the partition table assign ext3 to / and carry on 

you can put the ubuntu on extended partitions if you dual boot
yes even the swap

---

### Post by confused57 on 2007-03-14
You might be experiencing this bug in the live cd ubiquity installer:
[http://www.ubuntuforums.org/showpost.php?p=1700787&postcount=29](http://www.ubuntuforums.org/showpost.php?p=1700787&postcount=29)

---

### Post by raidlost on 2007-03-14
without to much technical

I found it works when you have [formatted] the file system before you start the install with ext2/3 (mkfs or the like)

---

### Post by newyawker on 2007-03-14
Thanks guys, I have ubuntu running and working fine.

---

