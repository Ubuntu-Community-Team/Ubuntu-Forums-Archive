---
title: "difference between ext2 and ext3"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-01-16
what is the difference between ext2 and ext3 filesystems?

---

### Post by Zack McCool on 2008-01-16
Journaling.  ext3 is ext2 with a journaling system to help maintain integrity.

---

### Post by blueridgedog on 2008-01-16
This is a too simple comparison:

[http://www.maenad.net/geek/di8k-debian/node29.html](http://www.maenad.net/geek/di8k-debian/node29.html)

[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

Basically ext3 is ext2 with journaling and is more or less a modern file system.  It is designed to maintain a journal of disk writes and to be more resilient in a crash.  It has a contemporary "competitor" called reiserfs

[http://en.wikipedia.org/wiki/ReiserFS](http://en.wikipedia.org/wiki/ReiserFS)

---

### Post by Matt26 on 2008-01-16
thanks for the information- which would be better for installing a vm machine onto?  i am planning to install Windows XP Pro on this disk and would like to know which file system to go with.

---

### Post by Zack McCool on 2008-01-16
ext3 for sure.  There is very little I would use ext2 for anymore...

---

