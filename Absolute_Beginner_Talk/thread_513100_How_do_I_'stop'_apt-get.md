---
title: "How do I 'stop' apt-get?"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by staib on 2007-07-30
Hi people,

A quick question... When I try and run Automatix I am getting an Alert message that says something like Apt-get is running - please close it and restart Automatix.

My questions are why is it running, and how do I stop it?  

I have checked System > Admin > System Monitor (Processes) but can't see anything that looks like Apt-get there...

Thanks,

Nick

---

### Post by Famicommie on 2007-07-30
If you have Synaptic open, Add/Remove Programs open, or are running a package installation from a terminal, then Automatix won't function properly. Make sure that all of those things are closed.

---

### Post by staib on 2007-07-30
Thanks Famicommie for the reply - but I have none of those open or running.  I just re-started the PC to check and I get the same error message....

How can I see if apt-get really is running?

Nick

---

### Post by Famicommie on 2007-07-30
Oh, I forgot to mention that the Update Manager is apt-get based. If you are downloading and installing updates, that would also lock out Automatix.

The best way to find out if apt-get is running is to open up a terminal and input the command: ```
ps aux | grep apt-get
``` That should check all running processes and filter them so that any with apt-get in the name are displayed. Note that "grep apt-get" will be returned in the results, but that itself is just the check for apt-get not apt-get itself.

Be careful with programs like Automatix; they have a tendency to do nasty things to systems down the road. If you are just using it to get video/audio codecs and programs that can be found in the repositories, you might want to consult [This Guide](http://doc.gwos.org/index.php/FeistyCust) instead.

---

### Post by rasesh_raz on 2007-07-30
i am not able to give apt-get command its giving the following error [root@ashwin ~]# apt-get install linux-tree
bash: apt-get: command not found

---

### Post by Vague on 2007-07-30
> **rasesh_raz said:**
> i am not able to give apt-get command its giving the following error [root@ashwin ~]# apt-get install linux-tree
bash: apt-get: command not found

The fact that you have a root console up suggests to me that you probably aren't using Ubuntu.  Which distro are you running?

---

