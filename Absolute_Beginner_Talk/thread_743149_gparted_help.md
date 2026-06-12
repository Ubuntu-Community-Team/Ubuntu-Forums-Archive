---
title: "gparted help"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by gitwick on 2008-04-02
i used gparted to partition the harddisk in my laptop i used the live cd its been like 15 mins since the operation started progress is zero and if i try to cancel it says that cancelling might cause serious damage to the file system.....:(:(:(:(:(:(:(:(

im trying to shrink a 70 gb to give me 20 gb free space

how much time does it usually take

---

### Post by bumanie on 2008-04-02
On the amount of information you've supplied, it's a bit hard to what is normal or abnormal. However it takes longer to shrink a partition if the partition has an already existing filesystem. If you are srinking and moving a partition it takes even longer, especially if the partition is moved closer to the start of the drive. Assuming there is a file system present, 15minutes is not overly long. I have had the experience of shifting and shrinking taking a couple of hours.

---

### Post by Diabolis on 2008-04-02
It is a slow process and it will be slower depending on the hardware capabilities of your pc. If is not showing any errors, leave it alone for a long while.

I suggest you to use the latest version of gparted. I even compiled it from source because it was giving me errors similar to this one.

---

### Post by gitwick on 2008-04-02
sorry for the double post i was getting a bit too worried
thanks yes my partition does have a lot of complications
fingers crossed

---

### Post by stchman on 2008-04-02
> **gitwick said:**
> i used gparted to partition the harddisk in my laptop i used the live cd its been like 15 mins since the operation started progress is zero and if i try to cancel it says that cancelling might cause serious damage to the file system.....:(:(:(:(:(:(:(:(

im trying to shrink a 70 gb to give me 20 gb free space

how much time does it usually take

Yes shrinking and growing partitions can take a long time.  Creation of new partitions from free space is fairly quick.  So the time is not out of the ordinary.

---

