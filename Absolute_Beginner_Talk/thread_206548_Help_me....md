---
title: "Help me..."
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by silvano on 2006-06-30
Hi, I am very new to linux and I just installed ubuntu yesterday. My hard disk is 80 Gb, so I installed windows on a primary partition of 7 Gb and then I started installing ubuntu. I mounted / on a primary partition and then I created an extended partition and divided it into 6 logical partition: one mapped with /usr, one with /home, one for windows and two more formatted with FAT32 so that I can use them to share data between linux and windows (right??). The problem is that I can't see the two FAT32 logical partitions when I am working with ubuntu. Insead I can use them with windows. Does somebody know what's the problem?
Thatnk you very much.
Silvano

---

### Post by jrattner on 2006-06-30
Run ```
sudo cfdisk 
``` 
Can you see the partitions? Do you need to mount them?

---

### Post by silvano on 2006-06-30
Yes, I can see all the partitions. What shell I do now? Thanks for helping me

---

### Post by Jagot on 2006-06-30
You need to mount them:

[https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html](https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html)

---

### Post by silvano on 2006-06-30
Hey it works!! Thank you very much! It's the first time a join a community and it is really nice to see people helping each other just for free. I think I am falling in love with linux and communities.:grin: 
Thanks again!

---

