---
title: "Two XOrg servers?"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by softtower on 2008-02-15
I have IBM/Lenovo ThinkPad T60p with ATI FireGL v5250 video card (if that matters) and I run Ubuntu 7.04.

I just noticed that System Monitor shows that I am running two instances of Xorg process (X server). One of them can always be safely killed, but another is "current".

My question is "why two"? The second one eats 22MB of perfectly good memory. How can I disable it?

---

### Post by spiderbatdad on 2008-02-15
Found this thread: [http://ubuntuforums.org/showthread.php?t=15564](http://ubuntuforums.org/showthread.php?t=15564)

offers at least one easy possible fix, and a couple of explanations.

Do you have remote login enabled?  Funny so many people are trying to learn how to run two xsessions.

---

### Post by amingv on 2008-02-15
I think it's because your laptop has 2 graphic outputs (the screen and the VGA port) and thus each one needs to be managed separately, 
A good test would be if you plug a monitor to it and then kill the other process, just to check; but that's on you...

---

### Post by softtower on 2008-02-16
Still unable to solve the problem. The first link does not seem to apply to me. Yes, I do have VGA and LCD monitors, but killing one of Xorgs does not do anything: it dies but everything keeps working smoothly.

It seems that GDM starts the first XOrg and then this XOrg creates a copy of itself (I looked at PIDs). Why? Where is it configured? 

Thank you.

---

### Post by softtower on 2008-02-16
I figured out the source of the problem. ATI strikes again! This proprietary driver of theirs is one piece of software...

It turns out ATI forks XOrg from within the driver:
[http://bugs.archlinux.org/task/8960](http://bugs.archlinux.org/task/8960)

---

### Post by k7my on 2008-03-07
me too same problem with u and want to post this same question too :), using ATI Driver 8.3(new)AIGLX and 8.40.4(old)XGL both also same, using X1250 mainboard graphics.

Hope can find a fix or solution soon.

---

