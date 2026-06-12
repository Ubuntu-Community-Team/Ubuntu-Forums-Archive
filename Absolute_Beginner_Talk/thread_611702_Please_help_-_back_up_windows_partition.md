---
title: "Please help - back up windows partition"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by luckylucky on 2007-11-13
A couple of months ago I came across an interesting article that using linux, and some linux software, that you could create a very easy complete backup of a windows partition, and if needed, restore it at some future time.  I think it makes some kind of mirror copy of the state.  I don't recall what it is called.

I've just reinstalled everything for dual boot (with Ubuntu of course) beautifully (hours & hours & hours of work to get XP & extras installed) and would love to make a copy of my fresh XP install so that I don't have to go through that again, and again, and again... etc...

Could anyone please tell me what the software was called and perhaps direct to a page to learn how to employ it?  Thanks in advance for any assistance!

---

### Post by hyper_ch on 2007-11-13
if you don't change the partition table and if you have enough room you could easily us "dd" to accomplish that. "dd" can make a byte-for-byte copy of your windows partition...

---

### Post by houstonbofh on 2007-11-13
Four things come to mind.

g4u - [http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)
g4l - [http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l) (May be a unlicensed copy of g4u) [http://www.feyrer.de/g4u/g4l.html](http://www.feyrer.de/g4u/g4l.html)
partimage - [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
clonezilla - [http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

---

### Post by luckylucky on 2007-11-13
Thank you all, I think that this might be what I need.  I'll be exploring those options now.  Thanks again!!!

---

### Post by Tux.Ice on 2007-11-13
i use clonezilla on gutsy gibbon

---

### Post by rubbsdecvik on 2007-11-13
I've used partimage with Gutsy.  I use [SystemRescueCD]("http://www.sysresccd.org/Main_Page") for the client.  I just create a shared folder on my gutsy machine and set up the client to find it.  I then just run the partimage client and it goes.  Takes a while, but it's completely saved.  It says it's experimental, but I haven't found a problem with it yet.

Hope that helps.

---

### Post by Inxsible on 2007-11-13
+ 1 for partimage using LiveCD

---

