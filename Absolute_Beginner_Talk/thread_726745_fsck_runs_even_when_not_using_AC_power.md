---
title: "fsck runs even when not using AC power"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by kikazaru on 2008-03-17
My laptop (Lenovo T60) frequently wastes a lot of time doing the fsck (particularly because I have several partitions) even when it is running on battery power. I looked at the checkfs script and it seems to have a check for ac power in it... (my scripting skills are a bit weak so I'm not sure exactly what's going on...) but even so it still runs the check when it boots on battery power.

Any suggestions (besides waiting for the next upgrade)?

---

### Post by ziroday on 2008-03-17
Have a look at this post here - [http://ubuntuforums.org/showthread.php?t=163500](http://ubuntuforums.org/showthread.php?t=163500) on how to disable fsck

---

### Post by erginemr on 2008-03-17
I don't know how you can instruct fsck to disable itself when running from battery, but for a more general control on fsck, you may try to give a go to an easy to use GUI program and a background service called **autofsck**:
[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

I have been using it for some time and it seems to fulfill its premise.

---

