---
title: "[SOLVED] Partitions for...."
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by Cariboo1938 on 2006-06-25
Thank you [COLOR="Magenta"] aysiu [/COLOR]for the help with KDE in Ubuntu!
I have another querstion: I have installed Libranet 3.0 and I want to switch to Ubuntu. When I installed Libranet, I partitioned my hard drive in that way that I created separate partitions for
/, Swap, Boot, Home, Usr and Var. I would like to do the same when I install Ubuntu. Or does the Ubuntu installer recognize these partitions?
Juergen:-k

---

### Post by aysiu on 2006-06-25
You can reuse the /home partition from Libranet to be /home for Ubuntu, but I would reformat it, as different distros use /home configuration files in different ways. Having a separate /home partition might come in handy for future Ubuntu reinstalls, though.

And, yes, there's a point during installation where you can select mount points. This will help you through the installation:
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---

### Post by Cariboo1938 on 2006-06-25
This is awesome, I never attended a forum with such fast and professional response, thank you [COLOR="Magenta"]aysiu[/COLOR]!
One more question: If I do the partitioning I have to make a decision which file system to use. In Libranet I used Reiser. Is this FS supported?
Juergen

---

### Post by aysiu on 2006-06-25
I think it *is* supported, but I've never used it with Ubuntu, so I don't know if there are any problems that come along with that.

If you ask Ubuntu to reformat a partition, though, it should automatically pick a filesystem (unless you specify otherwise) as Ext3.

---

