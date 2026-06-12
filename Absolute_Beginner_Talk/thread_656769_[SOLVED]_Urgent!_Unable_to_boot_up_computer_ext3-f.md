---
title: "[SOLVED] Urgent! Unable to boot up computer: ext3-fs and a readonly filesystem&amp;quot;"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by rouge568 on 2008-01-02
I am unable to get Ubuntu 7.10 to boot after a hard shutdown. Here is the last several lines of output: it will not progress beyond this even after a 30 minute wait. I am using puppy to write this, but it would only boot using only RAM.

```

EXT3-fs: INFO: recovery required on readonly filesystem.
EXT3-fs: write access will be enabled during recovery.
kjournald starting.  Commit interval 5 seconds
EXT3-fs: sda1: orphan cleanup on readonly fs 
```

How do I get my harddrive back? I have time-sensitive material on there that I need. Thanks in advance.

---

### Post by n8bounds on 2008-01-03
Since you're in Puppy, get a terminal and say 

sudo fsck.ext3 -v /dev/whatever

whatever = your ext3 inode block

---

### Post by spydon on 2008-01-03
I got the same thing for a couple of months ago and if you do these two commands you will be back to normal:

```
sudo e2fsck -f -y -v /dev/sda1
```
 /dev/sda1 can be something else on your computer...

```
sudo e2fsck -C0 -f -p -v /dev/sda1
```

---

### Post by rouge568 on 2008-01-03
Thank you **very** much. The system is stable and running well, and I got it fixed in time! I have been pleased and amazed at the ubuntuforum community and their speed, diligence, and helpfulness.   Thank you for making this a better place.


For future reference, the first command only worked for me if "-y" was removed, and sudo was not needed on Puppy.

---

### Post by spydon on 2008-01-03
> **rouge568 said:**
> Thank you **very** much. The system is stable and running well, and I got it fixed in time! I have been pleased and amazed at the ubuntuforum community and their speed, diligence, and helpfulness.   Thank you for making this a better place.


For future reference, the first command only worked for me if "-y" was removed, and sudo was not needed on Puppy.

You can thank ppl by pressing the star thingy on their posts ^^.
I'm glad it fixed your system too. :)

You can mark the thread solved by pressing "thread tools" and then "Mark thread as solved".

---

