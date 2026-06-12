---
title: "problems with a new hdd (SATA)"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by onesojourner on 2006-08-17
I can't figure this one out. I am having my mom dual boot ubuntu and xp. I have the  OSs on a 34g 1000rpm SATA. I just put in a 160g 7200rpm SATA. its set up in a raid just for storage. windows recognizes it and I created an extended partition. I formatted 50g for ntfs and I want to use the other 100g for ubuntu storage. in system > admin > disks I am showing 2 hdd. one shows 149g with my windows partition, ubuntu partion, swap and then it says 114g of free space. It will not let me fomrat the free space though. any ideas?

also I am not showing a second hdd below my first. it has no partitions and it doesn not display any other useful info about it.

so I just need to get about 100G for storage that ubuntu can read write. how do I do it?

---

### Post by onesojourner on 2006-08-22
Im giving this a little bump...

---

### Post by onesojourner on 2006-08-23
some one has to have some tips for me on this one.

---

### Post by rbmorse on 2006-08-23
You can't format free space. You have to create a partition, first...then format the partition.

---

### Post by onesojourner on 2006-08-23
I have it partitioned, by free space I just mean empty hdd space - an empty unfomatted partition.

---

### Post by rbmorse on 2006-08-23
OK...know how the system identifies the partition (it will likely be sda{some number}. Once you know that, use the command

sudo mkfs -t ext3 /dev/sdaX

replacing X with the number of the partition on drive sda. If the drive is something other than sda, adjust as appropriate. That will format the empty partition with the ext3 file system that Ubuntu can use. 

After the partition is formatted, it has to be mounted. Do you know how to do that? 

RBM

---

### Post by onesojourner on 2006-08-25
yep I know how to mount a partition. thanks for the help, it will likely be a few weeks be for I am back out to my moms place but I will give it a shot then. then I will update.

---

### Post by anaconda on 2006-08-25
> **onesojourner said:**
> I have the  OSs on a 34g 1000rpm SATA. I just put in a 160g 7200rpm SATA. its set up in a raid just for storage. windows recognizes it and I created an extended partition. I formatted 50g for ntfs and I want to use the other 100g for ubuntu storage. in system > admin > disks I am showing 2 hdd. one shows 149g with my windows partition, ubuntu partion, swap and then it says 114g of free space. It will not let me fomrat the free space though. any ideas?

Hmm..
What do you mean by: "its set up in a **raid** just for storage"
Do you have 2 exactly same partitions with same data, and raid mirroring them.. (that is how I understand raid, which is usually done with 2 hdd:s so that when 1 breaks no data is lost..)

How many partitions have you made to your hdd:s already. 4 primary-paritions is the maximum allowed for 1 hdd(extended partition is counted as 1 primary.). if you already have 4 partitions, you can't make new ones even if there is free space..

Sorry, but can't figure from your post how you have divided your hd:s. Can you post your parition table to here?
```

sudo sfdisk -l

```
If I remember correctly it prints you partition table from both disks.. If not then use:
```

sudo sfdisk -l /dev/sda
and
sudo sfdisk -l /dev/sdb

```

---

