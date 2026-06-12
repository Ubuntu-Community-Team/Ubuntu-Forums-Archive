---
title: "Base System"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by bosun on 2006-05-02
Hi, am new to unix so i got an ubuntu from a friend of mine,i was running windows on my system initally but when i tried to to install ubuntu so i will be able to dual boot i had got an error when i got to "Base System" and i decided to format my hard drive and install ubuntu only but i still got same erreo when i got to base system.
  Am wondering what am i doing wrong i need an urgent answer because my system is useless right now:confused:

---

### Post by mandrakethepenguin on 2006-05-02
Try getting a new CD, the one you have seems corrupt.  You can order them from shipit.ubuntu.com (although they will come in about 3 1/2 weeks). Also, the file system that it uses by default may be faulty, try an expert partitioner but use reiserfs, not XFS or JFS (ext2 isnt recommended either, journaled file systems are becoming standard). By the way, Linux is based on UNIX, an operating system built by AT&T Bell Labs in the 60's.

---

