---
title: "First apt-get upgrade failure"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by hoarsecourser on 2007-03-11
Okay, big time problems in my world.  I won't regale you with the horrid detail of the last few days, but I've (after many attempts) gotten Ubuntu Edgy onto my desktop, restarted and tried to do an apt-get upgrade.  It seems to not want me to do that.  It got to replacing evince 0.6.1-0ubuntu1 with /evince_0.6.1-0ubuntu1.2_i386.deb, started unpacking then gave me a

*** glibc detected*** /usr/bin/dpkg: corrupted double-linked list 0x08e76390 ***

line and a backtrace and memory map, neither of which I can make sense of (being a newbie).  Now I get the same "glibc detected" line with every "sudo apt-get update" or "upgrade" that I put in.  What did I do? (I may well have bad harddisk problems, that has been my headache for the past few days).  How can I get this to move forward?

---

### Post by eljalill on 2007-03-12
If you think this might be a problem of your harddisk, you could try the fsck command to check and repair that. Look into man page (man fsck) for syntax and the option you want .

If the problem persists, at least you know, what it is not about ... :)

---

