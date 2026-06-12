---
title: "How do I know if /home is on a separate partition?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Starks on 2007-10-27
If not, how do I make it a separate partition?

---

### Post by PartisanEntity on 2007-10-27
Creating a separate partition for home:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by vambo on 2007-10-27
To see if you have a separate partition, enter this in the terminal
```
mount | grep home
```
If you have a separate partition you'll get an output like this:
> /dev/sda4 on /home type ext3 (rw)
If you don't have a separate partition, there'll be no output.
NB
 This is just one of a dozen ways of doing it!

If you have to make one PartisanEntity's link is a really good guide.

---

### Post by markharding557 on 2007-10-27
> **Starks said:**
> If not, how do I make it a separate partition?

have a look in system monitor this shows all your drives and partitions and space on them

---

