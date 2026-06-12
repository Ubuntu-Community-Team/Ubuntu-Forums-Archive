---
title: "combining partitions"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by rickycodie on 2007-05-31
i have two ex3 partitions and would like to combine them. i have tried gparted but it has no feature like that.

---

### Post by Inxsible on 2007-05-31
I think you can do that in GParted. However, you will need to unmount the partitions first. Hopefully, you dont have any data on it.
 
1) Unmount the partitions
2) Start GParted from LiveCD
3) Create a new partition from the space available
 
 
 
Should be easy, unless I missed something in your question

---

### Post by rickycodie on 2007-05-31
i do have info on one of them. can i still do it?

---

### Post by empthollow on 2007-05-31
what you need to do is copy all of your data to the first partition ,then open gparted and delete the second partition, this will turn it into free space.   Click on the first partition and click the change/resize button, then drag the right arrow to then end of the drive.  click apply and you are on your way.  i recently had to do this to change filesystems bcz i'm trying to move my hard drive to a mac.  it has turned out to be quite the process converting to hfs+ but thanks to the ubuntu live cd i'm making it happen :)

---

