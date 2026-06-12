---
title: "my dapper box slowed way down, help!"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by bodhidharma on 2006-07-24
I just installed dapper on a brand-new homebuilt machine, it went
fine and I had a happy machine... for about a day.  Then I foolishly
installed every single interesting-looking package, and my system
went into some weird mode where the mouse is super slow: the problem
is all about *clicking*.  I mostly click and click and click and
somehow it doesn't see the clicks.  Eventually it does, though (which
is how I got here!).  Actually, if I click and hold for a *long* time
(variable, from a fraction of a second to several seconds), it eventually
sees the click.

Anyway, just wondering if anyone has seen this behavior before (the
clicks getting lost) and it is some configuration thing that got
messed up when I downloaded every piece of software under the sun....

Any help would be greatly appreciated!!!

Happy hacking....

---

### Post by s_h_a_d_o_w_s on 2006-07-24
System -> Preferences -> Mouse

Set Double-click timeout to the max right. Open synaptic and as  filter choose installed packages.

---

### Post by Kilz on 2006-07-24
> **bodhidharma said:**
> I just installed dapper on a brand-new homebuilt machine, it went
fine and I had a happy machine... for about a day.  Then I foolishly
installed every single interesting-looking package, and my system
went into some weird mode where the mouse is super slow: the problem
is all about *clicking*.  I mostly click and click and click and
somehow it doesn't see the clicks.  Eventually it does, though (which
is how I got here!).  Actually, if I click and hold for a *long* time
(variable, from a fraction of a second to several seconds), it eventually
sees the click.

Anyway, just wondering if anyone has seen this behavior before (the
clicks getting lost) and it is some configuration thing that got
messed up when I downloaded every piece of software under the sun....

Any help would be greatly appreciated!!!

Happy hacking....
Since its a pretty new install you may just want to reinstall to save banging your head into a wall. ](*,)

---

### Post by Sef on 2006-07-24
It sounds like something you downloaded in the cause of the problem.  I would back up your data and do a clean install.

---

### Post by nalmeth on 2006-07-24
If you can backtrace what you installed in when, you might be able to fix it my just removing them one at a time. 

Maybe there is a bug in one of the packages you installed, which has affected your xorg.

What kind of video card do you have? Have you installed any video drivers?

---

