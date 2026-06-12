---
title: "Mount: you must specify the filesystem type error message"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by darkworld on 2007-05-18
> mount -o loop /home/dark/Desktop/dsl-3.3.iso /mnt/iso

i started on loading dsl to a pen drive a few weeks back but failed so i shelved it. that was when I was running Mandriva. I have returned to the same tutorial weeks later, now running ubuntu, and its asking me to specify type. It didnt do this before. has mount command been updated or something?

Anyway i took a look at the man page and I can see the switch t for type but im not at all sure what im supposed to put in the command. Im using a  83 linux partition ext3

---

### Post by dstew on 2007-05-18
Yes, just use the -t switch. Your command would then be:```
mount -o loop -t ext3 /home/dark/Desktop/dsl-3.3.iso /mnt/iso
```
It might be that you had this file system mount command in fstab before, and it got the file system type from there. Maybe fstab has been changed, so now mount needs to know the type.

---

### Post by darkworld on 2007-05-18
Many thanks.

---

