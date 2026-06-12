---
title: "backup"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by gaddo on 2007-08-19
Hi Can someone give a novice some advice regarding backups?
The question is using sbackup can i backup to external drive and then restore from that drive
:confused:

---

### Post by HermanAB on 2007-08-19
First you have to decide on a backup strategy.  Windows users are used to backing up the whole system.  Unix users usually only back-up the data.  The reason being that when a system fails catastrophically, you are likely to build a completely new system, so a system backup likely won't work as the hardware is different.  Also, there is not much point in backing up Linux, since it is very easy to install and when you build a new system, you would likely want the latest version, not a 3 year old one.

Secondly, there are many tools to do backup, but when the system is newly built, the fancy tools tend to get in the way of restoring things, as you need to install and configure the fancy tool first before you can restore the backup, causing a chicken and egg problem.  Therefore experienced Unix users tend to favour simple command-line backup tools over fancy GUI tools, that presuppose having a working system.  The best backup tools is something that you can run off a general purpose live CD.

Therefore, most backup systems boil down to two mechanisms: 
a. tar
b. rsync

both of those are on all live CDs, so if you use one of the above, then you can restore a system using any old Live CD lying about.

Even the fancy GUI based pointy-clicky tools tend to use one of the above low level tools underneath all the glitz.

So, coming back to your question - yes, if you can mount a drive, then you can write a backup to it using tar or rsync.

Hope that helps!

Herman

---

### Post by mikeyphi on 2007-08-19
> **gaddo said:**
> Hi Can someone give a novice some advice regarding backups?
The question is using sbackup can i backup to external drive and then restore from that drive
:confused:

YES
I use sbackup for a daily backup to a seperate disc..you just have to be able to navigate to it during the setup process!

---

### Post by gaddo on 2007-08-19
Thanks for that and i take your point about backing the whole thing up when it is so easy to install.
I have just found a tool called sbackup and will try to backup just the data.
ps this is first time i have seen Linux only install 3 hours ago so i will stick with pointy-clicky stuff for a while.
Gaddo

---

