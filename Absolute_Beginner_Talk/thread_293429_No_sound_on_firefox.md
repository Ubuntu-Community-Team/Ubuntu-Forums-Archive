---
title: "No sound on firefox"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by shador on 2006-11-05
I'm having problems getting sound from firefox. When I try and watch clips from sites like youtube and google video i get the video but no sound. Any ideas why?

---

### Post by bulldog on 2006-11-05
Well I did read something about installing flash9 beta,which should take care of things.

Maybe you give it a try?

---

### Post by Iarwain ben-adar on 2006-11-05
> **shador said:**
> I'm having problems getting sound from firefox. When I try and watch clips from sites like youtube and google video i get the video but no sound. Any ideas why?

Hi,
well, a quick search gave me [this](http://ubuntuforums.org/showthread.php?t=238716&highlight=aoss)..


Iarwain

---

### Post by shador on 2006-11-05
Fixed now, checked the link and found that this command solved the problem: 

ln -s /tmp/.esd-1000 /tmp/.esd

Thanks for the help!

---

### Post by Iarwain ben-adar on 2006-11-06
No problem,
just remember that a quick search will probabely help you faster than we can :D


Iarwain

---

### Post by tekniche on 2006-11-12
So yea i tried that command and the link and it is coming up with "file exists" and i still get no sound in firefox. Any other suggestions?

---

