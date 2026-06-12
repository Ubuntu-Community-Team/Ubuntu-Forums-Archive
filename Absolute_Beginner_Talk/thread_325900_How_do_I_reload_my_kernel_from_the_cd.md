---
title: "How do I reload my kernel from the cd"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by caricc on 2006-12-26
I ran into some sort of problem I boot my laptop the other day and I can't get into my ubuntu edgy (6.10) partition. All I get is the bar hanging about 1/4 of the way thru then I get a flashing bar at the top of the screen. I get the same when I boot using the safe mode version too.  I can get to a command prompt. But I need your help on how to mount the cd rom drive and then command to reload the kernel. 

Thanks in advance.

---

### Post by diepruis on 2006-12-26
You could try:
```

sudo apt-cdrom add
sudo aptitude update
sudo aptitude reinstall linux-generic

```

---

