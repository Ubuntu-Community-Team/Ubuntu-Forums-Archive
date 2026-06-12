---
title: "Screenshot of QT parted"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by RAV TUX on 2006-04-22
on my old computer that I am currently running Breezy on I want to set up a dual boot of Ubuntu/Scientific Linux

I am including a screenshot of QTparted (by the way both QTparted and Gparted are available in the Synaptic Package Manager for newbies like me):

[http://static.flickr.com/50/133125010_a92992af90_o.png](http://static.flickr.com/50/133125010_a92992af90_o.png)

my question is with the space allowed...

1. do I have enough space to do dual boot on this system

2. if so how should I arrange my partitions

3. like this?
partitions............................what size?
1. Ubuntu............................?  
2. Scientific Linux.................?
3. data....................................?
4. ?........................................?

I am practicing setting up dual boot on this computer before I tackle my new computer (64bit/dual core)
:-k

---

### Post by catlett on 2006-04-22
Just run Scientific Linux and let it partiton. If it's like all the Linux installs I've done it will resize for you.
But if you want to do a partition ahead of time. Just make another 10gb ext3 partition before you run the Scientific install. Then let it install to that partition. It can use the swap that you already made.

You don't really need a data partition if they are both Linux installs. You can mount the partition the other OS is on when your running the other and have access to it's space and data. But if you really want to, make a FAT32 partition.This way  you don't get confused during install or when you want to figure out what each drive is labeled as (you can tell easier if they are different formats) for mounting. 10gb an OS should be fine. The rest you could make Data. I can't see your swap but a rule of thumb is twice your ram i.e. 256mb then 5122mb swap

PS.   [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)  This is a good how to although it is talking Windows/Ubuntu it is still a good reference point

---

### Post by dabear on 2006-04-22
Remember to create a seperate partition for your home, so that you can easily share your /home between both distros§

---

