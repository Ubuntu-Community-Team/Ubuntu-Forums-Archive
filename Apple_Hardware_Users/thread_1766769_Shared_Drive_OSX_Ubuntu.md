---
title: "Shared Drive OSX Ubuntu"
date: 2011-05-24
forum: Apple Hardware Users
---

### Post by thinktyler on 2011-05-24
The Wiki states:
> you cannot hibernate the system in e.g. ubuntu and then boot OSX, you will corrupt data this way.
If you have an unclean unmount, because suspend to ram fails on an empty battery or any other reason, ubuntu won't mount the disk in RW before a lengthy fsck.hfsplus (30minutes)
recently I noticed that bot OSX and ubuntu have to go through this filecheck everytime I boot the other system.

In Maverick are these still issues? The wiki seems to be dated somewhat, so I was wondering if anybody knew. I'm going to probably try tomorrow anyway if nobody has the answer.

---

### Post by thinktyler on 2011-05-25
All of the above still have problems, even in maverick. :(

---

