---
title: "I deleted Windows to make more room for Linux, :( but.."
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by Zaosyn on 2007-04-27
Well today I woke up and noticed that I had ALOT of spyware and viruses on Windows. I'm not the only one who uses my computer so I honestly don't know how it happened. I've just recently switched to Ubuntu and I love it. This was just the step I needed to finally leave Windows for good. I moved all my movies,music,photos,text files from my Windows partition onto my LInux one, and now I can finally delete my Windows partition with no regrets, however.. I don't know what to do to combine my empty space I was using for my Windows into the Linux partition to basically make 1 partition.

Here's a screenshot of Gparted and where I'm stuck at:
[http://img169.imageshack.us/img169/9799/screenshot5px5.png](http://img169.imageshack.us/img169/9799/screenshot5px5.png)

Should I turn the un-used space file format into "EXT3" Like Ubuntu uses? Or turn it to unformatted? I'm really confused.

---

### Post by ZeakStarwind on 2007-04-27
You should format that partition whenever you moved everything from your old partition. After you formated it, start partitioning it at what you said to ext3 and everything should be fine.

---

### Post by Scheater5 on 2007-04-27
Merely resize the partition with Ubuntu on it into the empty space, as opposed to creating a new partition.  This will be a time consuming process, and literally all of your files will be moved from the middle of your drive to the front.  Backup all your data first, as things do sometimes happen while partitioning, and make sure all drives are unmounted.

---

### Post by Zaosyn on 2007-04-27
Thanks! Quick question, it only allows for me to make it as primary, is that fine?

---

### Post by Scheater5 on 2007-04-27
Yes, that's fine.  "Primary" partitions simply mean it is a partition standing on its own - as opposed to an "extended" partition, which is analogous to a box in that it is a holding place for partitions inside it - called logical partitions.

---

### Post by ZeakStarwind on 2007-04-27
> **Zaosyn said:**
> Thanks! Quick question, it only allows for me to make it as primary, is that fine?

Not too sure. I know how it is when messing with the regular partitioning through windows, but can't quite say how linux would be the same or not.  Primary would make it the first thing that would make the computers bios to try and find the bootlogs in order to load your Operating system. I know the ubuntu cd running as Live has the features for partitioning also.  Sorry can't help you there. Still abit new to Linux.

Edit: Nevermind He said it. Thanks for the info mate. Will remember.

---

### Post by Sef on 2007-04-27
> Primary would make it the first thing that would make the computers bios to try and find the bootlogs in order to load your Operating system.

Not true for GNU/Linux.   When you install it, you choose what partition you want to be the default.   Windows must be on the first partition, so in dual boot systems, GNU/Linux is often on the second or third partition.

> I know the ubuntu cd running as Live has the features for partitioning also. 

I would recommend going to the [GParted]("http://gparted.sourceforge.net") site and downloading their latest updated partitioner.

---

### Post by ZeakStarwind on 2007-04-27
> **Sef said:**
> Not true for GNU/Linux.   When you install it, you choose what partition you want to be the default.   Windows must be on the first partition, so in dual boot systems, GNU/Linux is often on the second or third partition.



I would recommend going to the [GParted]("http://gparted.sourceforge.net") site and downloading their latest updated partitioner.

Thanks for that information Sef. I'll remember those. Still new to linux but learning fast.

---

### Post by louieb on 2007-04-27
Hello, I just look at the screen shot. I see you were using GParted from inside Ubuntu.  Which version?
Look like you are in good shape. Just use the Options I saw in the screen shot and you will be fine.
If you feel like going a little further I noticed you do not have a swap partition. 
You may want to slice your unallocated space into two (2) partitions. One for data, one for swap. You can play around with GParted **nothing happens until you press the apply button**. I have a small [partition page]("http://louboldt.com/ilinuxpart.htm") with some explanation of partition types and some links to find out more.

---

