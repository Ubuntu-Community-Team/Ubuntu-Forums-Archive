---
title: "How can I improve on a 4 minute boot-up with Dapper"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-06-26
Since  increasing the memory on my Samsung V25 laptop I've been able to install Ubuntu as a dual boot system with XP.   Xp works well, but Ububtu Dapper takes four minutes to boot up to the desktop and is very slow in use, even surfing the web is slowish.  What can I do to speed things up please. I'm wondering if I can turn off programs I'm not using to ease the load, so to speak. If this is possible how do I do this  please?

The laptop  has a Pentium 4 processor, 512 meg of RAM and a 30 Gig Hard drive partitioned equally for both XP and Ubuntu.

---

### Post by shearn89 on 2007-06-26
Not sure how to generally improve speed - on mine its fast. To kill processes do the following (in a terminal)...

If you know the name:
```
kill $(pgrep name)
```

To list processes and get the PID with which to kill the process:
```
ps -ef
sudo kill PID
```
The first command lists all running processes (scroll through to find the ones you want), the second kills that process. The PID is the second column, after the name of the user running it. The process is the right hand column.

---

### Post by mengfei on 2007-06-26
In terminal, run

sudo apt-get install bum

And then from there, go to System, Administration, Boot-Up Manager

Then turn off services you don't need.

WARNING: If you're not sure if you don't need a particular service, make sure you research it before turning it off. You can easily bungle your Ubuntu install if you turn off random services.

Good luck!

---

### Post by a.v.l on 2007-06-26
Thanks to you both for the help.

---

### Post by supersonicdarky on 2007-06-26
maybe your swap is too small?

---

### Post by pooper on 2007-06-26
im new. sorry if this is a load of sh!t suggestion, but is there such thing as defrag in ubuntu? (im still learning..) if not could run defrag through windos ?

---

### Post by happysmileman on 2007-06-26
No option for Defrag but it wouldn't affect a new install (I've been using Linux for over a year and drive hasn't gotten any fragments or gotten any slower so I don't think defrag is ever needed)

---

### Post by supersonicdarky on 2007-06-26
you generally dont need to defrag because the linux file system is more efficient than windows, and sort all the file chunks better. (i dont know the right term for it)

---

### Post by Austin_KW on 2007-06-27
To check what is slowing down your boot 
sudo apt-get install bootchart

and reboot

then look at the graphical chart in /var/log/bootchart/, you are looking for any problems where nothing is happening with inactive cpu no disk activity

For slow performance while running you want to check your memory stats with "free" and your cpu usage with "top".

---

