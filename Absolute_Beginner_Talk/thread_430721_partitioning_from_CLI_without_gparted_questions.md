---
title: "partitioning from CLI without gparted questions"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by dfreer on 2007-05-02
Hey everyone,

  So I got a new hard drive, and I have just under half of the HD full of data on an ext3 partition. It is located at the end of the drive, and I am trying to figure out how to repartition the the drive so that I have one large partition that takes up the entire drive. I prefer reiserfs, but from what I've read you can't resize reiserfs partitions.
  The hard drive is a 250GB drive and I have used 83GB, so I could create a new partition on the drive, copy the files over to the new partition, delete the old ext3 partition, and then resize the new one. Like I said, I would rather use reiserfs but if that is not an option I will use ext2/3.
   
   Most posts about partition I have read involve either using gparted or the live CD, both of which I can't do (This is on my server without a CD drive, and without a GUI). I'm would assume that gparted was the same as parted, but it seems it cannot resize or move ext3 partitions. I used this command:
```
sudo tune2fs -O^has_journal /dev/hdc3
```
To change my ext3 to ext2, but it still refuses to move/resize (I think it won't resize because it's at the end of the  HD). 

Does anyone have any experience repartitioning using the CLI? Or can someone point me to a guide I might have missed? Thanks in advance!

---

### Post by dfreer on 2007-05-03
Ok, so here's what I ended up doing. First, link to the guide I used:
[http://www.newsforge.com/article.pl?sid=03/10/07/2028234](http://www.newsforge.com/article.pl?sid=03/10/07/2028234)
Make sure to read the part near the bottom about how to use fdisk.


I created a reiserfs partition at the very beginning of the HD, so I had two partitions: the reiserfs filling the first half and ext2 filling the second half. I then moved all of my data off the ext2 onto the reiserfs, and deleted the ext2 partition using parted (after unmounting both partitions). 
Here's the tricky part: I then DELETED the reiserfs partition using fdisk, and then created a new partition that started at the exact same cylinder (in my case 1), and ended at the end of the hard drive. After writing the changes to the disk, I then used the command
```
sudo resize_reiserfs /dev/hdc1
```
To resize reiserfs to FILL the partition completely. Note it fills the partition, not the hard drive, so if you didn't use the full hard drive in fdisk you can still use this command. After remounting the partition, all of my data appears intact. Good Luck everyone else!

---

