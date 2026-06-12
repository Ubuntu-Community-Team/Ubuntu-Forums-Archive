---
title: "Dual Boot Ubuntu with XP"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by peterhuang913 on 2007-12-27
I've done this and I'm wonder what your Gparted looks like. Can anyone post a screenshot of their Gparted?

---

### Post by Dngrsone on 2007-12-27
Are you looking for anything in particular?  Or are you just curious to see if they all look the same?

---

### Post by kregg on 2007-12-27
The main thing is to have a ex2/ext3 partition, and a linux-swap on the hard disk.

You can do this by resizing the partition, and then adding a linux-swap and a ext3/ext2 partition.

Anyways, here is mine:
[ATTACH]54353[/ATTACH]

---

### Post by It_Was_Luck on 2007-12-27
Your in Luck... I did the exact thing, below is a photo of what my GParted program looked like right before I did it and installed it.

First off, my hard drive was 80GB, so I partitioned 10GB of it away, so my Primary Drive (which had windows on it) had 60GB, then I created a extended partition of 9.81GB then I used 8GB for Linux, then the last 1.81 for Swap. For your Linux partition use the mousepoint "/" without the quotes. 

Now if you plan on using a /home partition to save your files if you plan on updating, make another partition and give it the mousepoint "/home" inside your extended partition, this size can be anything you like, but remember this is where you'll saev your files, music, documents, everything.

[[IMG]http://img207.imageshack.us/img207/2796/screenshotng0.th.png[/IMG]]("http://img207.imageshack.us/my.php?image=screenshotng0.png")

Click that image to make it bigger. Once you partition it like that go into your installer and make it look like the image below, except be sure you tick the "Format" box for the partition your installing Linux too. Also,if you see that error thats below ignore it, it won't do a thing.

[[IMG]http://img145.imageshack.us/img145/2098/screenshot1oc4.th.png[/IMG]]("http://img145.imageshack.us/my.php?image=screenshot1oc4.png")

If you need any more help, ask.

-It Was Luck

---

### Post by peterhuang913 on 2007-12-27
Just curious.

Here's mines: [img]http://img403.imageshack.us/img403/7618/screenshotii2.png[/img]

Does it check out?

---

### Post by Dngrsone on 2007-12-27
It works...

One of my Slackware machines has something like eight partitions on it.  Of course, it was built some years ago, when FAT32 scratchpad partitions were more or less necessary to move data between Win and Linux.

---

