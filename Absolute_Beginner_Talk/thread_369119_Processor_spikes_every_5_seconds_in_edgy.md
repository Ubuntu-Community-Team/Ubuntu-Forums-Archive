---
title: "Processor spikes every 5 seconds in edgy"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2007-02-24
I noticed this today for the first time, last night while I was applying themes something crashed *(gnome panels disappeared, all the windows I had open were closed, until I was left with only the desktop wallpaper and nothing else, I had to restart into failsafe mode and there I was able to switch to a 'working' theme, the offending theme was called 'neutral')*.

Today, my Turion processor is switching between 800MHz and 1.60GHz about every five seconds apparently to me for no reason. Right now I only have Firefox running.

If I look at the running processes I have Firefox using up the most memory, approx 27mb.
As far as processor is concerned the highest is gnome system monitor is using 9% of CPU.

Anyone else notice this?

---

### Post by floke on 2007-02-24
It could be a root process - if you can get to a terminal, use 'top' to view all the running processes.  you can then log the PID number (I think its the 4-5 digit numbe on the left), and kill it with 'sudo kill -9 [PID number]' (not sure if you need to be root for this) to see if it helps.

---

