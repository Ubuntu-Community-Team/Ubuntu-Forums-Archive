---
title: "Problem starting X on new AMD 64"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by jluquette on 2005-11-27
Hey there everybody. I'm new to Linux, Ubuntu and AMD 64. I'm having a problem. I first made a DVD Live copy and it crashed just as X tried to begin. So, I made an install DVD and it crashed in the same spot. So, I made a CD install copy and the whole installation process went perfect until it booted up the first time and crashed right when it was asking me to login. Got an error saying that X didn't start - possibly because I didn't have it set up right. Well, I didn't do anything to set it up at all - was all automatic up to that point. I went to X's web site and read some trouble shooting info. Of course, there's NEVER a mention of the problem that YOU are having but I may have stumbled upon something that may relate here. It mentioned that X could only automatically recognize PCI and AGP. HMMMMM, I have PCI Express graphics built into my motherboard. Could it be that X cannot recognize this? Do any of you others have PCI Express? I really need some help from some one who knows something about UNIX, Ubuntu. Linux, AMD64:confused:  ...

---

### Post by ssam on 2005-11-27
sometimes the install does not configure X properly.

can you log into a terminal? (try pressing ctrl+alt+f1 to get one).

then run
```

sudo dpkg-reconfigure xserver-xorg

```
answer the questions, then
```

sudo /etc/init.d/gdm start

```

---

### Post by jluquette on 2005-11-27
So, you're pretty sure that it has nothing to do with the PCI Express?  After all, I have done this 4 times and it never worked - always crashing at the same point.  Also, if I can get to this screen, will the questions be something I could answer?

---

### Post by ssam on 2005-11-27
i am not completely sure if this will fix your problem, but it fixes a lot of similar problems, so its a good starting point.

most of the questions it will make a good guess at. you can try it a few times if you are not sure.

if it does not work then someone can suggest other things to try.

---

### Post by jluquette on 2005-11-27
Thanks for the help.  I think I was able to answer the questions correctly but unfortunately, got the same error - "X unable to start.  Probably not set up correctly."

---

### Post by ssam on 2005-11-28
ok

then i think this is likely to be a graphics driver problem. what graphics card do you have?

if you have a new nvidia card then maybe this will help [http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

---

