---
title: "Q About Filesystem Set up on Large Hard Drive"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by ianaaji on 2006-07-24
Okay, first of all, hello everyone, and thank you for your time.

Before my question, I'll give some specs, I'm running a 2.0 GHz Intel processor, I have a 40 gig hard drive, I have about 640 megs of ram, I think it's DDR. If you need any more info, I'll be happy to give it.

My question isn't really about Ubuntu, but I figured this is the best place for it. In the near future I'm going to be buying a 250 Gig hard drive. I currently have a 40 G drive in my computer, running Windows XP, Service Pack 2. My 40 gig drive is formatted in NTFS. I'm planning on installing Ubuntu on the new drive. My question is about how I should format the new drive. I'm obviously going to want some space that both OSs can read/write. From what I know, FAT32 is the only filesystem that both can read/write, but FAT32 is limited to 32 gig partitions, to my knowledge. I'm wondering if there is an option for a filesystem that can be read/written by Ubuntu and Win XP, and that supports large partitions.

---

### Post by aysiu on 2006-07-24
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html) will give you the full scoop.

For your particular situation, I'd use Ext3 and [http://www.fs-driver.org](http://www.fs-driver.org) to read/write it from Windows.

---

### Post by ianaaji on 2006-07-24
Wow, thank you for your prompt and helpful reply :) That information is great and solves my problem.

---

