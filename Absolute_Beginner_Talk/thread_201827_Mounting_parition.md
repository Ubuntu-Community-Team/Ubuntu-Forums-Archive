---
title: "Mounting parition"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by linux_student_user on 2006-06-22
Sorry if this seems like a repost - but maybe I wasnt clear enough - Ok if I have a ex3 partition how do I access it, or if the case may be mount it before accessing it. Thanks

Mike

---

### Post by aysiu on 2006-06-22
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by jvl on 2006-06-22
sudo mount -t ext3 /dev/hda1 /mount/point

substitute hda1 for your drive and partition
substitute mount point for a real directory

---

