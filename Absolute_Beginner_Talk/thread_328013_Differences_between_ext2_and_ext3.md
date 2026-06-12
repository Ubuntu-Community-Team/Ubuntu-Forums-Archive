---
title: "Differences between ext2 and ext3"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by Chop on 2006-12-30
Hello everyone. No gettin around it, but I'm green. So I have a few questions.  I'm currently running a Dapper and XP Pro dual boot.  I've sought XP access to my ext3 partition with (predictably) no luck.  It appears that ext2 can be accessed more reliably the "Ext2 Installable File System for Windows" software  also know as "fs-driver".  Maybe my line of logic is wrong, but it would seem allow more reliable access to my Linux partition if was mounted to the ext2 format.  Is this correct?  Can Dapper be run on an ext2 partition?  Or am I way off.  Any help would be always appreciated, be it  personal advice, directions to FAQS/how to's, or maybe I'm simply off point in my understanding.  Thanx always!

---

### Post by insane_alien on 2006-12-30
dapper could be run on a ext2 partition but fs-driver is capable of handling ext3 as ext3 can be mounted as an ext2 partition with no problems.

---

### Post by Sef on 2006-12-30
Ext2 and Ext3 are the same except that ext3 has journaling.


From[ Linux ext3 FAQ]("http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html"):

> Q: What is ext3?

Ext3 is a journaling filesystem developed by Stephen Tweedie. It is compatible to ext2 filesystems; actually you can look at it as an ext2 filesystem with a journal file. The journaling capability means no more waiting for fsck's or worrying about metadata corruption. What is most noticeable is that you can switch back and forth between ext2 and ext3 on a partition without any problem: it is just a matter of giving the mount command the right filesystem type.


---

### Post by Chop on 2006-12-30
Thanks for the responses, perhaps I'm running the package wrong under XP.  Would either of you be able to direct me to a clear and reasonably basic user guide/troubleshooter for configuring and running the FS-Driver/IFS .exe in XP?

---

### Post by Sef on 2006-12-30
> Thanks for the responses, perhaps I'm running the package wrong under XP. Would either of you be able to direct me to a clear and reasonably basic user guide/troubleshooter for configuring and running the FS-Driver/IFS .exe in XP?

Could you please start a new thread for that in the Windows Forum (Forum Community > Other OS Talk > Windows Discussions.   Thank you.

---

