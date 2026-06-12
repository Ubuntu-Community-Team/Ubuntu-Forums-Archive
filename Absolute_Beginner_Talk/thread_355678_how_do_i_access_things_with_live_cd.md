---
title: "how do i access things with live cd"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by iiker on 2007-02-07
i need to change some config files in my ubuntu. the problem is that i can't get into my ubuntu. (made some changes and now it can't load grafical UI) now what i need is to gain access to my files using live cd. is it possible?

---

### Post by g3k0 on 2007-02-07
ermmmmmmm somewhere in the back of my brain i think I can find something somewhat useful...

I believe you have to mount your partition with / on it....  ehhhh something like that...  Cant think of the code perhaps a good Samaritan will stop by and give you the code.

---

### Post by iiker on 2007-02-07
well that wasn't helpful :(

---

### Post by g3k0 on 2007-02-07
lol umm i think its something along the lines of this though it might not be hda3 check your partitioner in the install
mount /dev/hda3 /directoryname

---

### Post by CCBalla10 on 2007-02-07
> **iiker said:**
> well that wasn't helpful :(

iiker, i had a problem a little while back where i need to use the live cd to change things on my system.  I had to mount my partition...here is a link to the thread I started...on the second page is where i solved it....hope it helps you somewhat....

```
http://www.ubuntuforums.org/showthread.php?t=331523
```

---

### Post by bodhi.zazen on 2007-02-07
```
sudo mkdir /media/ubuntu
sudo mount /dev/hdxy /media/ubuntu
```

Where /dev/hdxy is your ubuntu partition, /dev/hda2 perhaps

If you do not know your ubuntu partition, in a terminal enter:```
sudo fdisk -l
``` To list your partitions 8)

---

