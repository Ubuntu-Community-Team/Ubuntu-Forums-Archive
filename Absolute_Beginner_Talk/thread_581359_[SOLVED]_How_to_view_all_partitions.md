---
title: "[SOLVED] How to view all partitions"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by mramsey on 2007-10-19
How do i view all of my partitions? I want to make sure everything installed as i wanted to.

---

### Post by LowSky on 2007-10-19
program called gparted will help.

its on the live CD

---

### Post by twiceasworn on 2007-10-19
Or alternatively you can just do 

```
df -h
```

That will also tell you how much space is being used etc.

---

### Post by mahiyar on 2007-10-19
>> sudo fdisk -l for getting both the mounted and unmounted partition.

---

### Post by ronmarley1 on 2007-10-19
System -->Administration -->Partition Editor will also show drive info.
You can run the same app. from a terminal by typing:
```
gksudo gparted
```

---

### Post by mramsey on 2007-10-21
> **twiceasworn said:**
> Or alternatively you can just do 

```
df -h
```

That will also tell you how much space is being used etc.


Thats what I was after!:)

---

