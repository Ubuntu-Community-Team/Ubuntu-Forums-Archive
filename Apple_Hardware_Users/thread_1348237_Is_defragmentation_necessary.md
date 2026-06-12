---
title: "Is defragmentation necessary?"
date: 2009-12-07
forum: Apple Hardware Users
---

### Post by gray9504 on 2009-12-07
Hi, I just got Karmic to dual boot on my MacBook 2.1, and was wondering what kind of system maintenance Ubuntu requires?  For instance, is disk fragmentation a very big concern?  The forums claim that it is not for the ext3 filesystem, but I am using ext4 for my installation of Ubuntu, and I would rather not leave my computer to it's own devices even if I was using ext3.  Is fragmentation a concern for ext4, and what programs or commands should I use to defragment?


I know that as a Mac user, the very idea of rigorous system maintenance is something of a foreign idea, but any help that I could get with this question would be greatly appreciated.

---

### Post by adamdotanderson on 2009-12-07
My understanding is that, since it is a journalized filesystem (like OS X's) it simply does not require or benefit from the defragmentation process but I could be wrong.

---

### Post by oswaldkelso on 2009-12-07
I was curious so googled it for you :) 

[http://polishlinux.org/apps/cli/ext4-defragmentation-with-e4defrag/](http://polishlinux.org/apps/cli/ext4-defragmentation-with-e4defrag/)
[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

---

### Post by gray9504 on 2009-12-08
Actually, Google and Wikipedia were the first places I checked, but thank you for the links nonetheless.  It's sounds like this isn't something I really need to worry about.  However, if I could ask one other question about maintenance, are there any commands like Mac's periodic daily weekly monthly scripts I can use, or is that also not necessary?

---

### Post by Gen2ly on 2009-12-08
As for as defragmentation goes, you should be fine.  The ext3 and 4 filesystems find the first open spot that has enough size and writes the file to disk continuously.  So, for the most part, you are good.  The only place you are going to have problems is when you disk space gets low and ext3 and ext4 will begin to fragment files.  There are a few defragers in linux but no of real notoriety.  Ext4 is supposed be getting one (I believe in the next kernel) but have heard very little about it.  

For maintainance, Ubuntu pretty much will handle what you need.  These are cron jobs, and you can see what the jobs are by typing:

```
crontab -e
```

---

### Post by gray9504 on 2009-12-08
Alright, thank you for the help!

---

