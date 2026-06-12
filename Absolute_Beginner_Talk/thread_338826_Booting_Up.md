---
title: "Booting Up"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by hegpau on 2007-01-15
i installed Kubuntu 6.06 (ya i no 6.10 is out) but i was trying to see if 6.06 works and it has same problem with 6.10.. when it goes to the screen where it loads all the stuff then it gets to loading hardware.. it just stops and wont load anything? is there some reason it wont load my hardware

---

### Post by Ecthelion on 2007-01-16
You probably haven't looked in your logs...?
Since I suspect you can't acces your disk since Ubuntu doesn't work, you'll have to do it the hard way.
Or do you also have an other OS installed on the same computer.
If you have an other OS installed on your computer, just go to the root dir of your ubuntu, and go to /var/log/
Then look at these files:
auth.log
daemon.log
kern.log
messages
syslog
user.log
Xorg.0.log

Normally you should find a crash report or something in those... or so I hope...

If you don't have an other OS on your pc, tell me...
I'll tell how to acces your disk via the livecd then.
(I hope the livecd does work on your pc...???)

---

