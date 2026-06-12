---
title: "messed up my xorg.conf need help getting it back to normal"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by dragnazz5.0 on 2007-04-03
well lets just say i was trying something that i shouldnt have been because it has never worked before.  but anyways, i cannot get fiesty to load because my xorg file has some bad stuff in it.  i can boot into fvwm, fluxbox, e17 but i cant change the xorg file from these for whatever reason.  any help is greatly appreciated.  thanks

---

### Post by spin2cool on 2007-04-03
ctrl-alt-F1 should get you back into a command line (or just boot into recovery mode).  Then use your favorite command-line editor to make the changes to your xorg.conf.

You can also start from scratch by typing "sudo dpkg-reconfigure xserver-xorg"  That will lead you steb by step back through the set up.

---

### Post by dragnazz5.0 on 2007-04-04
well the reconfiguring the xorg file worked....well i can log into gnome now but i cant use my mouse.  it will scroll but it wont click on anything and my keyboard wont work either.  guess i need to redo it and see what happens.  thanks for the help

---

