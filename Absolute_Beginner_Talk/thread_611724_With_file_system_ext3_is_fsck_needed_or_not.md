---
title: "With file system ext3 is fsck needed or not?"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-11-13
I would like to know if fsck is still needed with a journal file system like ext3.

---

### Post by reckless2k2 on 2007-11-13
yes. sorry for so short but yes. fsck alone will explain that. you can look into ext3 as well.

---

### Post by rbprogrammer on 2007-11-13
i'm no expert on this matter, but i would believe so.. my guess is that it acts as a second line of defense for when something might go wrong.  if using the journal cannot help, then maybe fsck can.

---

### Post by Inxsible on 2007-11-13
you dont have to worry about it much. After every 30 or so mounts, fsck is forced on that partition.

So you might sometimes see that when you boot up that it does fsck on one or more partitions.

---

### Post by philinux on 2007-11-13
It's just that I read somewhere, cant remember now, that a journalled file system like ext3 does not need fsck ie e2fsck as this was designed for ext2.

---

### Post by philinux on 2007-11-13
Bump - I'd love to know

---

### Post by philinux on 2007-11-16
I guess we dont need to use fsck at all, acording to this.

[http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html](http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html)

---

### Post by atlfalcons866 on 2007-11-16
did you read
Q: If a system shutdown hard, even with journaling is it at all necessary to run e2fsck?

Theodore Ts'o said:

It's best to just always run e2fsck. [...]
E2fsck will run the journal automatically, and if the filesystem is otherwise clean, it skip doing a full filesystem check.
If the filesystem is not clean (because during the previous run the kernel noticed some filesystem inconsistencies), e2fsck will automatically do a full check if it is necessary.
If you have multiple disks, fsck will run multiple e2fsck processes in parallel, thus speeding up your boot sequence than if you let the kernel replay the journal for each filesystem when it tries to mount it, since then the journal replays will be done sequentially, instead of in parallel.

---

### Post by philinux on 2007-11-17
Seems like the bottom line for me is run it manually.

---

