---
title: "[SOLVED] Quick problem to solve (installing)"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by linuxbeatswin on 2008-04-02
Hi, and good morning (depending on where you are).
I was updating my Ubuntu, and noticed that there was a warning that I would be installing software that couldn't be authenticated. Of course, you folks who are very experienced with Ubuntu have probably seen it before. So, my question is- what should I do about that software? Is it just a message that is there to be on the safe side?

I just don't want to do anything stupid to my system.

Thank you!

---

### Post by A$h X on 2008-04-02
Where did you get the programs that aren't authnticated? If they are from a reputable source, then you can probably install them without fear of them being malware. You should try and get most of your programs from the repos, that way you can be sure that they are safe to use.:)

---

### Post by taavikko on 2008-04-02
It would be good to know what was the package?
If you're enabled unsupported repositories that may well be the case.
For unauthenticated things to upgrade.
Things dont install themselves.

But if it is something you've personally already installed....
```
tail -30 /var/log/dpkg.log
```
should give better info

---

### Post by stefangr1 on 2008-04-02
I think he's getting them trough the repros. You get that sometimes with very new packages that aren't in their stable version yet, like some kde4 packages.

---

### Post by linuxbeatswin on 2008-04-02
> **stefangr1 said:**
> I think he's getting them trough the repros. You get that sometimes with very new packages that aren't in their stable version yet, like some kde4 packages.

Yes, all I did was click on that familiar "orange star" at the top right of the screen, and updated from there. So, the packages are okay as long as they came from the "orange star"? (all hail the Ubuntu "orange star"!)  I need sleep.....

I apologize for this VERY noob question, I have spent so much time with this system, and don't want to damage it. Thank you all very much for taking the time to answer my little post.

---

