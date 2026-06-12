---
title: "Installation/Partitioning issues"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by wldstrm on 2007-04-23
I posted this problem in the installation forums, but Im desperate and still a Linux newb so I thought i would post here as well:

My harddrive is a 80gig that had two partitions.  I had a partition with approx 35gigs for windows xp and a partition with approx 45gigs for games and personal files.  I had  installed Ubuntu Edgey last week before Feisty was released.  At taht time i shaved 10gigs off of my personal file partition for my Edgey install.  I used 1gig of that for swap.  This was all done using Gparted on the live cd.  I liked Ubuntu quite well in the limited time i spent using it.  

I wanted to upgrade to Feisty.  I decided i wanted a clean install for Feisty and that i wanted to try out Xubuntu this time, so i deleted out my old Edgey and swap partitions from the Feisty live cd using Gparted.  Now when i try to use the 10gigs of unallocated space for my ext partition and swap partitions i receive the following error when attempted the ext3 partition:  

/dev/sd6 is mounted; will not make a filesystem here!

my listed drives are: 
dev/sda1 - Windows  nfts format
/dev/sda2 - extended
/dev/sda5 - Personal nfts format

I have no idea where sda 3 and 4 are, or why it tells me that sda6 is mounted.  I have no idea what sda 6 is.  It has been suggested to me to try the gparted live cd instead using gparted inside of the Xubuntu live cd.  I am trying that right now.  Hopefully someone can help me because I really like using Linux so far and i cant afford to shave any more off of my personal or window partitions.

---

### Post by lamalex on 2007-04-23
are you inside of linux when you do it or using the livecd? if you're currently using the OS you can't format it. Try using the gparted livecd (not to be confused with gparted on the ubuntu livecd)

---

### Post by wldstrm on 2007-04-24
zazen66 also suggested this in my other post.  using the gparted live cd everything worked like a charm.  i just repartitioned, then rebooted using hte xubuntu live cd, piece of cake.  thanks guys im one step closer to being windows free!

---

### Post by whymany on 2007-04-26
If you only have the xubuntu cd and you are having problems with the ext 3 partition giving errors when you try to delete a previous windows xp partition you can use gpartition to delete it and install xubuntu. just type in: sudo gpartition. the app will come up and delete it. you may have to format it to ext 3 first and then delete it but it will work after that. 
this will fix a problem with installing xubuntu on a computer with windows xp that you want to get rid of.

---

