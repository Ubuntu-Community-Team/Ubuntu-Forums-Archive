---
title: "Virtual Desktop question"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by mikej_96 on 2007-04-28
This is probably the dumbest question I have ever asked on here. But here it goes.  How can I keep certain windows from showing up on the window list of the panels on every desktop. 

For example, if i have gedit open, and I change desktops, it still shows up on the windows list on my panel, even though I don't have anything open on it. Then when I click on it, it brings me back to the original desktop that gedit is on.  Not every program does this, but some do and it can be very annoying. I have 8 instances of gedit open on 1 desktop, and when i change desktops, they are all still down there. 

I can't figure out how to fix this... I know it sounds like a dumb question. 

I am also running the feisty desktop effects if that matters at all.

---

### Post by viciouslime on 2007-04-28
If you right click the title bar and click "always on visible desktop", that should toggle the effect. However, what you are describing isn't exactly how that feature works, i.e. when you then click the application it shouldn't switch to the other desktop, it should act like you are running two identical programs on two different desktops.

In other words, if this does not work, then it is probably just a bug with compiz: it isn't the most stable thing yet.

---

### Post by mikej_96 on 2007-04-28
I do not get that option on the title bar. I think it is because of compiz..... I will disable compiz and see if it helps... Thanks for the quick reply.

---

### Post by viciouslime on 2007-04-28
> **mikej_96 said:**
> I do not get that option on the title bar. I think it is because of compiz..... I will disable compiz and see if it helps... Thanks for the quick reply.

No problem, if you find using metacity does fix the problem, i.e. it is just a bug in compiz. you might like to file abug report using launchpad. Also, you could try beryl as an alternative to compiz.

---

### Post by orb9220 on 2007-04-28
Right-click window list applet and select prefs. Right there on the behavior there is Show windows from Current workspaces and Show windows from all. Check show windows from current.

then under window grouping.
select Never group windows,

---

### Post by mikej_96 on 2007-04-28
Well i guess with compiz enabled you do not get these options, or at least I dont anyway. There is no "move to workspace right or left" or "show on all workspaces anywhere." I disabed compiz and sure enough, the "show on current workspace" option was checked for gedit. I unchecked it and enabled compiz again. No more problem. Thanks.

---

### Post by mikej_96 on 2007-04-28
Well, it worked for a while I guess. But then all of a sudden it started happening again. Its wierd how compiz only gives the maximize, minimize, move and close options when you right click on the title bar. Definatly a compiz bug.

---

### Post by Incie83 on 2007-07-23
Hey, this thread pointed me to a solution for my gedit problem! 

It seems to me that, when desktop effects are enabled, the properties of the gedit window are set to 'Always on visible workspace' by default! Quite strange for a default setting (especially if you're not familiar with the window options by right clicking the title bar).

EDIT: This problem is thought to be a Compiz bug originally, it's reported as bug #93622. I think the best workaround at the moment is to use **Devil's Pie**. mikej_96, maybe this would help you as well?

---

