---
title: "My computer is horrendously slow..."
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by nzk on 2007-07-10
Alright, Ubuntu was working fine for me up until recently (as far as I remember). It was snappy and quick with GNOME, even with only 512mb of RAM. Well, now it's so slow I cannot play an mp3 and use Firefox at the same time without skipping and stopping. I doubled my RAM to 1GB but it's the same.

I tried KDE and XFCE but both are very slow. 

My specs are:
3.46ghz P4
1GB RAM
ATI Mobility Radeon 9800
etc.


I would really like to start being able to watch movies and play music on my computer. What can I do? I have a Kubuntu 7.10 CD burnt but I don't want to reinstall (or install it to a different partition) unless I can backup my data/mount another partition to transfer files.


What can I do?

I have EXA disabled, I tried both "ati" and "radeon" drivers in xorg.conf, etc.

---

### Post by AlexenderReez on 2007-07-10
try this


> [http://news.softpedia.com/news/Improve-Performance-in-Ubuntu-Edgy-47261.shtml](http://news.softpedia.com/news/Improve-Performance-in-Ubuntu-Edgy-47261.shtml)

---

### Post by UnixAnt on 2007-07-10
I would perform some basic performance monitoring to begin with.

Try running the following:

# top <---This is a real time process manager

# ps -ef | pg  <---this wil tell you how much CPU time processes are using

# free <---this will tell you how much memory (physical and virtual) is being used

You should be able to see obvious resource hogs from these.  I have found that laptops with wi-fi cards tend to become unstable from time to time and really impact performance.

Let us know if you find any culprits. ;)

---

### Post by nzk on 2007-07-10
Trust me, it has nothing to do with load or anything. I've been looking at top for a long time with nothing out of the ordinary.

---

### Post by alienexplorers on 2007-07-10
I am running an old K6-III 450  and Ubuntu runs at a pretty good speed.  Don't think your processor or memory are causing the slowdown.  Not sure about ATI graphic drivers.

---

### Post by UnixAnt on 2007-07-10
> **nzk said:**
> Trust me, it has nothing to do with load or anything. I've been looking at top for a long time with nothing out of the ordinary.

Fair enough.

How about the following then: Instal gkrellm or conky, reboot your box and monitor with one of  these apps.  Does simply doing nothing cause the system to report anything out of the ordinary?  A jump in CPU usage, memory, network activity, etc?

Also it might be worth running a tail -f on /var/log/messages and /var/log/dmesg and see what is being reported.

Any use?

---

