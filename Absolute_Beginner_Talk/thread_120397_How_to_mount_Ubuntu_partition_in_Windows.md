---
title: "How to mount Ubuntu partition in Windows?"
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by Cesium on 2006-01-21
I figured out how to mount my Windows partition in Ubuntu (which is great!), but I cannot find how to mount my Ubuntu partition in Windows?  Am I able to mount my Ubuntu partition in Windows?  If so, how?  thanks!

---

### Post by ubuntu27 on 2006-01-21
Try this: [http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)

---

### Post by jonathanm on 2006-01-21
this really depends on what format your hard drive is that ubuntu is on.  if your drive is not in a format that windows supports - fat (most likely), iso9660 or ntfs (very unlikely) then windows will not be able to read/write it.  There may be others that windows supports but if your hard drive is one of the popular linux formats (reiserfs, ext2/3) then it is not yet possible as far as i am aware

---

### Post by midwinter on 2006-01-21
Yeah, you just need some software.  

Also often recommended is [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Cesium on 2006-01-21
Thanks everyone.  Any recommendations on which of the two programs is better?  

Thanks again!

---

