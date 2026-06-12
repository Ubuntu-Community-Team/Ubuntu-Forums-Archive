---
title: "Need help, virtual ram."
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by net wrek on 2008-01-28
Ok, I run ubuntu 7.10, and would like to know how to convert some of my hardrive space into virtual ram to increase system performance. I've dicked around, searched a bit, but to no avail, and would like some assistance on this.

Thanks for any help.

---

### Post by Cypher on 2008-01-28
Even if you were to find something that will allow you to use some of your HD space as virtual ram, it's in no way going to increase your system performance. If anything, it's going to remain the same or make it worse. Access to system memory is many times faster than the HD and so that's your bottleneck.

You're better of getting more memory..

---

### Post by bump_ on 2008-01-28
When you were installing ubuntu, did you choose the "Guided" option for setting up partitions? If so, you already have a swap partition to act as virtual memory. Check by running

```
sudo fdisk -l
```
in the terminal

---

### Post by emarkd on 2008-01-28
You probably already have a swap partition (virtual memory).  Check it by running

```
sudo fdisk -l | grep swap
```

---

### Post by net wrek on 2008-01-28
Thanks for the help guys, much appreciated.

---

