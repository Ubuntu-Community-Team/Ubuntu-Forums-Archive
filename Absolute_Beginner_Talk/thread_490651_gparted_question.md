---
title: "gparted question"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by rgraves22 on 2007-07-02
I have linux installed on my main HDD, I want to setup a dual boot with the beta of gusty. Im running gparted, but cannot partition the 30GB of freespace I have.. 

Any thoughts?

---

### Post by annda on 2007-07-02
how many primary partitions do you have? you can't have more than 4.

consider creating an extended partition with logical ones for gutsy and shared swap (you need only one for all the linuxes, so you can delete the old swap partition and create new extended with swap and gutsy ext3)

---

### Post by Bartender on 2007-07-02
Are you using the stand-alone [GPartedLiveCD]("http://gparted.sourceforge.net/livecd.php") or the partitioner on the Gutsy LiveCD?
Try using the GParted LiveCD.  Also, it's not enuf to unallocate the free space.  You'll have to wipe it clean as unformatted.  Or try formatting it as ext3.

---

### Post by rgraves22 on 2007-10-11
I only have 1 partition, a 40GB HDD with Ubuntu 7.04 now...

---

### Post by oilchangeguy on 2007-10-11
> **rgraves22 said:**
> I have linux installed on my main HDD, I want to setup a dual boot with the beta of gusty. Im running gparted, but cannot partition the 30GB of freespace I have.. 

Any thoughts?

aside from the partition problem you're having. why not wait til the final version of 7.10 is out. you'll likely have problems with beta software.

---

