---
title: "Updates always advisable??"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by timbosity on 2008-02-12
This has probably been covered here there and everywhere. By default, is it always better to blindly run apt-get update? or to go through what the update GUI suggest for updates and pick and choose what appears important?

Just curious really as to how important these updates are. I installed Xubuntu back in early december and I suppose I havent really updated anything since then. Should I get updating? I noticed a few funny things going on like a packagei wanted to install didnt find an X11 application... Could this be update problemo??

thanks for any input/ideas/enlightening thoughts

---

### Post by LaRoza on 2008-02-12
I always do them all, no problems.

If there happens to be a problem with an update, you'll hear about it probably, but otherwise, don't worry about it.

---

### Post by oedha on 2008-02-12
i am not really sure about the correct menu in xubuntu
but in ubuntu....system - administration - software sources
then system -administratiorn - update manager

---

### Post by JoshuaRL on 2008-02-12
Well, it all depends.  Are you strapped for HD room?  Do you have a monthly limit on how much you can download?  Or do you just not feel like it?

Whatever the issues are, I would strongly suggest to at least update everything that is a security update.  That's just good OS procedure.  As far as the other stuff, it's less important.  But usually programs will work better with each other and Ubuntu/Xubuntu if they're updated.

I can't tell you exactly if the X11 issue is update-related without the error in front of me, but I would assume it was.

BTW, your avatar is sweet.

---

### Post by spiderbatdad on 2008-02-12
I try to stick to security updates, though occasionally a program I want to install requires updated libs, or whatever. I can do it the hard way, searching the dependencies out and installing them, or sudo apt-get update...assuming what I need is in the repos...a big assumption sometimes.  Upgrades definitely pose the greatest impact to a "stable" system.  So, I guess I don't have a great answer, but I do read through, rather than just closing my eyes and clicking...go. 

I have set Administration>>Software Sources>>Updates only to "important security updates."

---

### Post by doorknob60 on 2008-02-12
I always install every update (including backports and preposed) and I've had no problems :) Also sudo apt-get update doesn't actually update your software, just the list of software that it CAN get. But, sudo apt-get upgrade will update your programs.

---

### Post by timbosity on 2008-02-13
thanks to all. Thats what I meant; apt-get upgrade :)
did it anyway all 148 of them... (thats why I was asking by the way cos there appeared to be so many of them... It seems to have solved all the little glitches that were popping up here and there (except wireless obviously...). It also looks/feels like theres a little speed improvement on things like openoffice... maybe just my imagination...
Anyway, hdd isnt that much of a problem although I only have 3.5GB free space. It might be time to get rid of that XP partition altogether and have a Xubuntu only machine. Just waiting for wireless to work...[http://ubuntuforums.org/showthread.php?t=687290](http://ubuntuforums.org/showthread.php?t=687290)
any help on that one would be muchos welcome...

---

