---
title: "partition"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by phanipalagummi on 2008-02-28
i am very new to linux

can i create 6 drives of same mount point

i.e
/home  10GB
/home  10GB
/home  10GB
/home  10GB
/home  10GB
/home  10GB

---

### Post by Duck2006 on 2008-02-28
This link may help.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by ajgreeny on 2008-02-28
Why on earth do you need 6 different /home drives, or do you mean home partitions?  All the users on a computer will go into the same /home partition, each as a separate /home/username folder in nautilus, so there is little point in having separate /home partitions.

To answer you question more directly, however, you can have as many drives (real separate drives, not partitions, on your machine as the hardware will allow to be connected.  On a single drive, however, you can only have a max of 4 primary partitions, so to get 6 partitions on one drive you would need to make an extended partition to put at least some of the six into.  I repeat, however, there is no real need normally to do this at all.  By all means make a separate /home partition when you install, but then allow the system to put all users into that one partition.

---

