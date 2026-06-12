---
title: "partition resize help"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by tjb891 on 2006-12-15
I jusk shrunk my ntfs windows partition and now I want to be able to undesrtuctively rezize my ubuntu ext3 main partition to take care of the free space. Can I do this inside from Ubuntu? I have a Gpparted livecd but it won't let me resize my linux partition. It will only let me make it smaller not larger. Does my Bios prevent this?

---

### Post by taurus on 2006-12-15
What's the output of this command?

```
fdisk -l
```

---

### Post by Sef on 2006-12-15
> I have a Gpparted livecd but it won't let me resize my linux partition.

Do you have the most recent copy of GParted?  If I remember correctly, the older editions of GParted, you couldn't add onto the beginning of the partition.  You had to add on to the end of it.  I think that is not true anymore with the newer editions.

Check out GParted's [How to Resize Partition]("http://gparted.sourceforge.net/larry/resize/resizing.htm").

---

