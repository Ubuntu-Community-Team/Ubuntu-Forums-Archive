---
title: "Hard disk efficiency"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by infernus_crusher on 2008-02-07
I'm kinda confused how much hard disk space should be left unused? Norton recommends at least 25% (under that and it gives you warning) but is it necessary?

I mean, with 160 GB HD, u have to leave 40 GB unused. That seems a lot to me.

---

### Post by Tatty on 2008-02-07
Its certainly a good idea to leave at least 20% of your hard disk unused.

In Linux, you should never need to defragment the hard drive as the ext3 filesystem is really good at not fragmenting files.  

However this all goes wrong if you use more than around 80% of the hard drive as there is not enough blank space left to store complete files, so it has to start fragmenting the bits across the drive.

Im not sure what percentage you should keep free with a windows system, but i imagine it would probably be about the same.


For a really good explanation of fragmentation look at this link: [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting")

---

### Post by Paqman on 2008-02-07
> **Tatty said:**
> 
Im not sure what percentage you should keep free with a windows system, but i imagine it would probably be about the same.


My Windows defrag utility spits out warnings about reduced defrag performance if it has less than 15% free.

---

