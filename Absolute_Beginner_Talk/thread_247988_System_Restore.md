---
title: "System Restore"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by pteri498 on 2006-08-31
Is there an Ubuntu equivilent to Windows's System Restore? Because that would be really useful whenever I do something that somehow messes with another program. Case in point, scim no longer detects anthy, so if anyone knows how to solve this problem specifically, that'd be great.:confused:

---

### Post by kidders on 2006-09-03
The answer is no, I'm afraid :( Linux systems all work too differently than eachother for there to be a consistent enough way to do such a thing. Windows succeeds (somewhat!) because it permits no meaningful variation in the way important things are done.

One thing you *can* do though is back up your /etc directory on occasion. This is where all Linuxes keep the majority of your system settings. There may well be a smarter way of undoing changes, but this strikes me as one that will work well no matter what.

[LIST=1]
[*]Back up /etc to your home directory: **cp -dpR /etc ~/etc-20060903**
[*]Do some risky updates or some such
[*]Compare the old /etc to the new one: **diff /etc ~/etc-20060903**
[/LIST]

"diff" is a useful tool that shows you differences between things. It's highly configurable. Here, you can use it to identify alterations an "apt-get install" made, one of which might have broken something. Of course, this is unlikely to happen unless you install packages yourself, without telling apt-get about it.

I hope this helps!

---

### Post by Drakkor on 2006-09-03
I cheat and use a windows program called Acronis True Image,and create regular copies of my whole second hard drive , the one with Ubuntu on it.
that way ,if I screw up  Ubuntu, I can just restore the whole thing in about 10 minutes! :)
Edit: You want to make the backup when everything's fine and working so you can go back to that working state.

---

### Post by MaximB on 2006-09-03
one other thing you can do when you screw up ubuntu
is to go back to your last Kernel (never tried if it works).
when you start your PC - there are several Kernel choices you can choose from to start ubuntu.

---

