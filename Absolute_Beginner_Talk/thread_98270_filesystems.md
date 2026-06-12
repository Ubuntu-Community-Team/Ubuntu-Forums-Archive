---
title: "filesystems"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by slrafal on 2005-12-02
Does someone know where I can get a good explanation about the differences between all the linux filesystems.

ex: Why use ext3 instead of ReiserFS

---

### Post by AndyCooll on 2005-12-02
Try this thread: [http://www.ubuntuforums.org/showthread.php?t=92817&highlight=reiserfs+ext3]("http://www.ubuntuforums.org/showthread.php?t=92817&highlight=reiserfs+ext3")

Also some links about various filesystems here:
ext2: [http://e2fsprogs.sourceforge.net/ext2intro.html](http://e2fsprogs.sourceforge.net/ext2intro.html)
ext3: [http://www.redhat.com/support/wpape...ext3/index.html](http://www.redhat.com/support/wpape...ext3/index.html)
xfs: [http://oss.sgi.com/projects/xfs/](http://oss.sgi.com/projects/xfs/)
reiserfs: [http://www.namesys.com/](http://www.namesys.com/)

:cool:

---

### Post by poptones on 2005-12-02
ext3 is journaled but if you shutdown improperly you're still likely to end up having to run a ten minute fdisk on restart. With reiser it may take a few seconds to replay the last journal and, unless something went terribly wrong, you're right back up and running.

I've tried several and I no longer would trust my data to anything but reiserfs. I've accidentally wiped out hundreds of megabytes of partition info and, using the reiserfs diagnostic tools, have been able to recover pretty much everything that wasn't overwritten. One may have to pour through gigabytes of lost&found directories, but I have found it's always been able to recover.

---

