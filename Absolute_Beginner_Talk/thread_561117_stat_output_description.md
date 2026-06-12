---
title: "stat output description"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by jackloo on 2007-09-27
I am really sorry for stupid question.
Can someone explain what does mean the last column in stat output:
$ stat e
  File: `e'
  Size: 873             Blocks: 8          IO Block: 4096   regular file
Device: 804h/2052d      Inode: 2500667     Links: 1
Access: (0744/-rwxr--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2007-09-27 10:00:31.000000000 +0700
Modify: 2007-08-25 23:38:45.000000000 +0700
Change: 2007-08-25 23:38:45.000000000 +0700

I mean +0700

Thanks in advance!

---

### Post by justleen on 2007-09-27
```
man stat 
```


my guess is "last time of change¨, time offset +0700

---

### Post by jackloo on 2007-09-27
Thanks for reply.
I've tried man stat and info stat already,

* %x - Time of last access
* %X - Time of last access as seconds since Epoch
* %y - Time of last modification
* %Y - Time of last modification as seconds since Epoch
* %z - Time of last change
* %Z - Time of last change as seconds since Epoch

But there is no exact answer what it is, and that value is always the same on all files

---

