---
title: "Install Issues"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by jcizzle on 2008-01-10
Hey All, I'm pretty new to Ubuntu and Linux altogether.

I seem to be having some issues getting it installed on my laptop (Sony Vaio PCG-K33). As of right now there is no OS installed on the laptop because I wiped XP after it was giving me issues. The most common problem I seem to be encountering is I will occasionally get to a log in screen that requires a password after booting off the liveCD (although nothing is installed, so I have no log/pass - ubuntu/<none> or ubuntu/ubuntu doesn't work, as well as no user/pass). 

Now, the problem seems to be the downloading/burning process. I've used just about every version of Ubuntu I can find to try to get it installed (7.1 live/alternate, 6.06 live/alternate, 5.10, etc.). On the 7.1 version (when running CD check) I always get an error in one file (doesn't say which). I've used different CDs and even a DVD. I've also burned them on two different machines. Everything encounters some sort of a problem and it seems to be different everytime I try to install. Sometimes I can get to a certain screen, othertimes I can't get that far, so it's difficult for me to say I get hung up at one point. I've even used different mirrors to download the iso from. I've tried noapci and noacpi, but neither work and not in combination either. 

It doesn't seem to be an issue with my laptop's CD drive because it boots fine and I've installed Windows a few weeks ago (only to find I've used up my # of times I can use my key). 

This really has me scratching my head as I've tried every combination I can think of. :confused:

Any help is much appreciated!

---

### Post by robbieo11 on 2008-01-10
You have to make sure you are burning the iso to disc very slowly. Max is 4x speed. When it gets to grub, have it check the disc integrity.

---

### Post by jcizzle on 2008-01-10
> **robbieo11 said:**
> You have to make sure you are burning the iso to disc very slowly. Max is 4x speed. When it gets to grub, have it check the disc integrity.

I forgot to mention it, but I have been using the slowest speed possible. Usually it's 4x, but sometimes it only lets me do 8x. :(

---

### Post by eolson on 2008-01-10
Let's try the easy things first.

Clean the lens on your cd drive.  They sometimes pick up some dust or gunk of some sort.  Try a q tip with some eyeglass cleaner.  If you don't have that rubbing alchohol.

---

### Post by jcizzle on 2008-01-10
> **eolson said:**
> Let's try the easy things first.

Clean the lens on your cd drive.  They sometimes pick up some dust or gunk of some sort.  Try a q tip with some eyeglass cleaner.  If you don't have that rubbing alchohol.

Thanks for the tip, never thought of that. I usually forget the simple stuff like that. :)

Tried it and it didn't work though. Got past the little bar dancing back and forth, but the bar after that (the one that usually goes to 100%) didn't move past 5% (eyeballing it). I rebooted after that and got to the login screen I seem to hit more often than not, but can't get past it because I don't have a login. There was an error message in between the bar hitting 100% and reaching the login screen, but it ended quickly and I couldn't make out much. Something about locale error. Just shows how abstract the issue seems to be that I can do something one reboot that didn't happen the time before. :(

---

### Post by eolson on 2008-01-10
Assuming the cd's are good, and it's hard to believe all of them would be bad,  it's starting to sound like maybe a memory problem.  Can you restart the machine and keep hitting the escape key.  That should stop the boot process at the grub menu where you can select the memory test option?  Let it run several times.

---

### Post by jcizzle on 2008-01-10
> **eolson said:**
> Assuming the cd's are good, and it's hard to believe all of them would be bad,  it's starting to sound like maybe a memory problem.  Can you restart the machine and keep hitting the escape key.  That should stop the boot process at the grub menu where you can select the memory test option?  Let it run several times.

Yeah, seems like you're probably right. I'm unsure how to read the test, but I'm getting an awful lot of red , which seem to be failing addresses. I take it this is a hardware issue then?

---

### Post by eolson on 2008-01-10
Sounds like it.  Just to make sure I'm running it on my laptop and no red all blue background and grey or white letters (I'm partially color blind).

---

### Post by jcizzle on 2008-01-10
> **eolson said:**
> Sounds like it.

Gah what a shame, thanks for the help though!

---

### Post by eolson on 2008-01-10
No problem.

---

