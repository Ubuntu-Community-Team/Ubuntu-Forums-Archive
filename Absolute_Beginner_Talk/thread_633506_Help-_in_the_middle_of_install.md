---
title: "Help- in the middle of install"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Rezistik on 2007-12-06
I'm installing ubuntu right now and am stuck at the partitioning window, I DO NOT WANT TO USE THE ENTIRE drive however only 2 options are available...use entire drive, or use largest continuous space..both expect me to already have partitioned the drive...but gparted wont partition it so I was hoping that I would be able to do that during this install

I was hoping for something like in this tutorial

[http://img379.imageshack.us/my.php?image=feistydual06rw5.png](http://img379.imageshack.us/my.php?image=feistydual06rw5.png)
([http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing))
But I don't see anything like that, will someone please help me.


 I feel like such a noob :(

---

### Post by betes on 2007-12-06
Are you trying to set up a dual boot? Do you already have another OS installed?

---

### Post by Rezistik on 2007-12-06
yes I have two hard drives one has windows xp the other is my media hard drive that I was going to put a ubuntu partition on both are 40 gigs. I was hoping to give 10 gigs to ubuntu on my media drive.

I would really like to dual boot so I can eventually move to ubuntu.

---

### Post by MQMike on 2007-12-06
You need to select the "Manual" method of install/partitioning -- it is the last one listed.

Then, in Step 6, click the Advanced button at lower right, and there you may specify where to put GRUB.

---

### Post by Rezistik on 2007-12-06
will editing those partitions wipe m drives?? Because I cant do that.

---

### Post by MQMike on 2007-12-06
You must be careful, yes!  Always must be careful when doing any partition editing in any manner.  Back up any important partitions and/or data first.

In my opinion, ideally, you really should do the partitioning as a separate first step before running the installer, and do so using GParted Live CD, to be clear and safe (and relaxed while you o it!):

GParted:   [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
GParted how-to:   [http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

