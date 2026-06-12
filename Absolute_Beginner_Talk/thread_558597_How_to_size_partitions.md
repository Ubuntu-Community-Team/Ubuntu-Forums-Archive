---
title: "How to size partitions?"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by Robin.Muilwijk on 2007-09-24
I successfully tested Ubuntu on both my Desktop and Laptop, so I am ready to switch from MS to Ubuntu now.

Both machines have a hard disk of 160Gb. I was wondering what the best size would be for all partitions. I would be using the following partitions: [https://help.ubuntu.com/7.04/installation-guide/i386/apcs03.html](https://help.ubuntu.com/7.04/installation-guide/i386/apcs03.html)

> For multi-user systems or systems with lots of disk space, it's best to put /usr, /var, /tmp, and /home each on their own partitions separate from the / partition.

Thanks for any help.

---

### Post by rolnics on 2007-09-24
My root partition has about 10Gb /home has about 50Gb and the swap 2Gb along with WinXP on a 10Gb with room to expand.

But I would give the /home partition the most space and 10Gb for /root is fine. As for the /usr and /var a couple of Gb's maybe, I'm not sure on that and the /tmp I would do as they suggest 50Mb maybe 100Mb on the safe side.

---

### Post by crossedout on 2007-09-24
I've always used separate / (root), /home and swap partitions and never needed to have partitions for /usr, /var, /tmp.  Probably because I like starting completely fresh from time to time.  Having the separate /home partition will allow you to reinstall or fresh install a new version without having to backup all your settings and files (although you should anyway).  The swap size should be roughly double your ram.  10gig should be plenty for the / partition.

-Xout

---

### Post by rsambuca on 2007-09-24
To be perfectly honest, I think the advice on that page is just way to complex for most users needs.  If you have a 160GB drive, I would recommend 10 to 20GB for your root partition, 1 or 2 GB for your swap, and the rest for your /home.

---

### Post by laidback on 2007-09-24
rsamuca is right, no more than 20Gb for root (/) partition. In fact 10Gb would probably be enough if you also have a /home partition.

---

### Post by psusi on 2007-09-24
There is some benefit to having a separate /home partition, but I usually don't bother.  There is certainly no reason to have a /var and /usr partition, and you most definitely do NOT want a /tmp partition because that is normally mounted as a tmpfs and kept in ram/swap.  

Filing a bug report against that page now.

---

### Post by Robin.Muilwijk on 2007-09-24
Thanks for all the feedback.

Is there a specificreason why NOT to setup different partitions for /usr, /var, /tmp ?

---

### Post by vanadium on 2007-09-24
Not to make things more complex than really needed. A drawback of separate partitions is that flexibility is lost in the usage of space. If it is all on the same partition, all free space is commonly available for all needs. With split partitions, only the free space on one particular partition is available and you can get into situations where one partition runs out of space while the other has still plenty of room.

For personal systems, I tend to recommend simplicity: a root and a swap. With a larger drive such as 160 GB, you could perhaps go for a root, a home and a swap, but I would not take that any further. For larger volumes, you might include an additional volume for data.

Building servers is a different matter, and there the many different partitions for different system directories makes sense.

---

### Post by Robin.Muilwijk on 2007-09-25
Thanks, that sure is a clear explanation. I'll be moving soon, leaving MS behind me, and I'll setup the HD's with your advice. Thanks.

---

