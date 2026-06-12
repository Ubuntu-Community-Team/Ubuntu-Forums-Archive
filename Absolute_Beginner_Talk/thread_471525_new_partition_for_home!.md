---
title: "new partition for /home!"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by jonie.pan on 2007-06-12
hi, guys. i'm newbie here. and one question about how to mount /home to a patition exlusively and save all my already configure, you know, i didn't mount /home to an exclusive partition before. Thanks a lot.

---

### Post by Skrynesaver on 2007-06-12
Have you a spare partition that you intend to use as your new /home ?
If so you should mount it on /media/partition-name and copy everything under /home over maintaining permisions "cp -Rp /home/* /media/partition-name"
Then after checking that all went well 
```

ls -lR /home >home.orig
ls -lR /media/partition-name>home.new
diff home.orig home.new

```
unmount the partition, delete the contents of /home, add the partition to /etc/fstab and mount -a.

If this raises more questions feel free to ask ;)

---

### Post by Tux Aubrey on 2007-06-12
As above - but you might want to read up on the pluses and minusees of a separate /home.  
[URL="http://ubuntuforums.org/showthread.php?&t=300246"]
This thread[/URL] has some interesting alternative views.

And, of course, Asiyu has a page on it [here.]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by jonie.pan on 2007-06-12
Thanks, Skrynesaver. I really like to do a separative patition for my /home. so as your saying, I would try that way. Thanks again!

---

### Post by zvacet on 2007-06-12
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by jonie.pan on 2007-06-12
I made it done. thanks everyone.
as did these following: 
1) Create a partition

2) Copy /home to that partition

3) Remove/rename your old /home folder

4) Mount the /home partition in a new /home folder

---

### Post by DracoPsycho on 2007-06-12
Yup, but you should also edit your /etc/fstab file so it will be mounted at startup if you hadn't done so ;)

---

