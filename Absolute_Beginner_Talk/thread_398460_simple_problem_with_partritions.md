---
title: "simple problem with partritions"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by Sasa_Ivanovic on 2007-04-01
I have two HDD.
on first one which is 120 GB i store my data.
on second one i have two partrions one with windows 42 GB and the other one with Ubuntu 110 GB.
First i installed Windows, then Ubuntu and everything worked fine. I like Ubuntu more then Windows... then after some time Windows couldn't boot 'cause of some virus. So i used Ubuntu alone for a couple of months ( and i really started to like it ). Now i have some kind of program that i need to run on Windows. The question is :
if i format the space where windows is and install windows xp there again would i be able to boot GRUB and choose which OS i want ?

Since i've heard some people talking that you have to install Windows first and then Ubuntu in order to be able to choose with GRUB. In that case is there some kind of solution... what should i do ...[-o<

---

### Post by tommcd on 2007-04-01
If you reinstall windows it will overwrite the MBR and grub with it. Grub can be reinstalled with the ubuntu live CD:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
Or from the ubuntu alternate CD:
[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)
For everything you would ever want to know about grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by SentientFluid on 2007-04-01
When you reinstall Windows, it **is** going to take over the MBR and you'll only be able to boot into Windows after that.  It's greedy like that.  However, you can restore Grub afterwards if you have a LiveCD.  Check out [this article]("http://ubuntuforums.org/showthread.php?t=24113"), as well as [this one]("http://www.ubuntuforums.org/showthread.php?t=224351"), and choose the one which works best for you.

---

### Post by Sasa_Ivanovic on 2007-04-01
thanks

---

