---
title: "Writing on NTFS"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by Mazen on 2006-10-09
i already posted in this subject but didn't get a clear answer...
is there any software that runs in Ubuntu and from which i can read/write on my NTFS partition? any commands i can use?
thanks

---

### Post by halitech on 2006-10-09
by default you can read an NTFS partition but it is not recommended to write to it. I do on occasion simply  by mounting the drive as read/write but it can corrupt system data on NTFS so don't go by what is currenly working for me as gospel that it will work for you.

---

### Post by bodhi.zazen on 2006-10-09
> **Mazen said:**
> i already posted in this subject but didn't get a clear answer...
is there any software that runs in Ubuntu and from which i can read/write on my NTFS partition? any commands i can use?
thanks

[Read/Write NTFS (ntfs-3g)](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by comppsyco on 2006-10-09
Check this out: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by lemonsCC on 2006-10-09
If you must look at this thread:[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g]("http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g")

EDIT:  To the post above.  Mounting an NTFS partition doesn't mean you can write to it

---

### Post by iampoch on 2006-10-10
I've been using ntfs-3g for quite some time copying, editing, and creating files and it's never conked out on me yet. I highly recommend it.

---

