---
title: "Scary Install question in install attempt"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by diogenes2 on 2007-11-26
Hi people,
No matter how I read it, the install options for 7.10 seem to tell me that all my existing Windoze partitions will be lost. 
I did a prior simple auto install of 7.04 to an old Sony notebook with no trouble at all and have a nice dualboot all done by "following the dots" nothing special.

I am using a Live Disk of 7.10 and would really like to put it on my external  new 500G USB Drive, but it doesn't want to go there. 
Running "Live" it can't find the sound or the Internet. 
 
Tried to install "manually" but the Partition options are a bit scary - threats of losing all. 

Question 1: Would the sound/internet problem be influenced by running Live or not?
Question 2: Do I have to manually configure something re Internet when the mini-network ( The Sony and this box) it  is part of runs everything fine?
Question 3: I do have lots of space on my drives, am happy to do an auto install if it won't delete everything, how do I make sure of that?

Thanks!
10 years later - still determined to go Linux.  All I need now is DragonDictate to convert](*,)

---

### Post by miltonr on 2007-11-26
I would recommend creating an additional partition onto which you can install your Ubuntu distro.

---

### Post by perce on 2007-11-26
> **diogenes2 said:**
> 

Question 1: Would the sound/internet problem be influenced by running Live or not?



Probably not, so you should expect the same problems after the install. You might want to search the forum about your network card and your sound card to be sure that your problems can be fixed

> 
Question 2: Do I have to manually configure something re Internet when the mini-network ( The Sony and this box) it  is part of runs everything fine?


Pardon?

> 
Question 3: I do have lots of space on my drives, am happy to do an auto install if it won't delete everything, how do I make sure of that?


If you have an empty partition you'll see an option of installing in that partition, If your empty space is in a non empty partition, you'll have to make a partition first before installing. I think the installer has the possibility of resizing partitions. I don't know how safe it is (never tried) but if you want to use it I suggest that you:

1) backup all your files
2) be prepared to reinstall Windows if something goes wrong (so have Windows CD and drivers CD at hand)
2) defrag the partition you are going to resize, so that all data are at the beginning and 
all free space is at the end.

---

### Post by nikoPSK on 2007-11-26
Yes create a partition. If you run a live cd then choose install it can create a partition for you. Same with the alternate pc. Or better yet get wubi. It will install as a windows app then you can choose windows or wubi. ^^

---

