---
title: "external hard drive question :?"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by DUNC4N on 2006-12-08
With the success of installing ubuntu on my PC(dual boot), I've decided to partition my laptop hard drive and start using that with ubuntu also. I realy need to read some books.


***Problem***

I plug in my external hard drive, and it pops up on the desktop. I can open it, and copy stuff, but I can't edit, anything. It says read-only due to premissions.

I would like to edit, word/excell documents with open office. Hopfully moving totally toward, linux. Obviously I have a lot to learn.


Thanks.
-Dunc4n

---

### Post by taurus on 2006-12-08
Is it ntfs or fat32 filesystem?  Here's a guide on how to mount windows partition/drive...

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by riven0 on 2006-12-08
> **DUNC4N said:**
> With the success of installing ubuntu on my PC(dual boot), I've decided to partition my laptop hard drive and start using that with ubuntu also. I realy need to read some books.


***Problem***

I plug in my external hard drive, and it pops up on the desktop. I can open it, and copy stuff, but I can't edit, anything. It says read-only due to premissions.

I would like to edit, word/excell documents with open office. Hopfully moving totally toward, linux. Obviously I have a lot to learn.


Thanks.
-Dunc4n

I think this could be a problem with the hard drive's file format. Is it in the ntfs (windows) file system?

EDIT: taurus got to it before me. :D

---

### Post by gn2 on 2006-12-08
Your external hard drive needs to have a Linux compatible file system.

Linux can read from, but not write to NTFS unless you add software to do so. I would advise against as it can be unreliable.

If it is NTFS I would suggest changing it to FAT32, which will work natively with Windows and Linux

---

### Post by DUNC4N on 2006-12-08
Thanks I will look that over.

The drive is a 40gb ntfs. (old laptop hard drive)

BTW, how did I get "spilled the beans" under my name? lol

-dunc4n

***Edit***

Dang you guys are fast. Many many thanks :)

---

