---
title: "Is there a Linux partition editor that can resize the partition I am in?"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Fonon on 2007-09-01
Same as above.  More importantly, is it free?  The Gparted Live CDwon't work for some reason :(  It claims it can't accolate enough memory, which makes it crash at the startup...even though I have a gig of RAM.

If there is none, is there a way to emulae Acronis or Partition Magic on Cross Over or Cedega?

---

### Post by Dr Small on 2007-09-01
Do you have Ubuntu installed?
```
sudo apt-get install gparted
```

And try it from inside Ubuntu, while not using all of your memory on the RAM.

Dr Small

---

### Post by nonewmsgs on 2007-09-01
use your ubuntu live cd and install and run gparted.  as long as you're just using the livecd it isnt really runnng off the drives so they arent mounted.

---

### Post by bone2006 on 2007-09-01
I've used gparted liveCD the latest on a system recently with 64MB of ram, so since you have 1GB of ram it seems to be something else.  I'd run memtest86+ to double check that your ram is alright.  
Try an older or new version of gparted as well.  I had a version that gave me trouble before, so you should maybe look at one of the oldest version gparted has posted and see if that works out for you.

you can use gparted inside ubuntu with the partitions that aren't mounted.

---

