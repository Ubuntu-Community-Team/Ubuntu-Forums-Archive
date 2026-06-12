---
title: "Planning out partitions; Vista and Ubuntu (does FS-Drive work on Vista?)"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by Gadren on 2007-04-16
With the notebook I'm getting soon, I'm planning on setting up the following partitions:

Vista and games: 60GB
Shared space (/home): 70GB
Ubuntu: 28GB
Swap space: 2GB

Total: 160GB

Now, I'm not horribly in love with this setup, so if you have suggestions, please let me know.  For example, how much do I actually need for just Ubuntu?

But here's the actual question:
I have my Ubuntu, and my Vista+games...the shared space is what I'm wondering about.
I'd like to have it also be my /home (unless there's a reason to not have it that way)...but it also needs to be accessible from both Vista and Ubuntu.  Now, from [this partitioning guide](http://www.psychocats.net/ubuntu/partitioning), it seems like this is what I essentially want.
[img]http://www.psychocats.net/ubuntu/images/partitioning5.png[/img]

However, this one was recommended because of FS-Drive, which allows access to ext3 partitions from Windows.
**Does FS-Drive work in Vista?**

If not, then what should I do?  Should I end up having a separate /home and shared space (with /home being ext3 and the sharespace being FAT32)?

---

### Post by Happy_Man on 2007-04-16
Try it. If it doesn't, then you just have to keep /home in /, and have a separate FAT32 partiton for sharing.

---

