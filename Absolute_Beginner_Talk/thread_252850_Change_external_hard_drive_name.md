---
title: "Change external hard drive name"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by jd65pl on 2006-09-07
Anyone know how I might change the name of my external hard drive?

Thanks

J

---

### Post by Omnios on 2006-09-07
What do you mean by changing name. If you mean in the menu and destop Ubuntu uses the mount point file name as the drive name on the desktop and menu. For example I use /documents as a mount point so it is named docuements

---

### Post by monktbd on 2006-09-07
depends what filesystem you use on it.

ext2/ext3 partitions can be changed with 
e2label

for changing fat32 partitions you need to do it with mtools (google should give you hints how to do it)
edit: found it 
[http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/](http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/)


i dont know if it is possible for ntfs partitions.

---

### Post by jd65pl on 2006-09-07
Yeah it maybe a shed load easier for me to just plug it into one of my windoze boxes then.

Cheers anyway

---

