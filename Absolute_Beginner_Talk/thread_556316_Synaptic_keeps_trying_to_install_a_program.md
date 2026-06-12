---
title: "Synaptic keeps trying to install a program"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by Diranttt on 2007-09-21
I installed Java with NetBeans, but the installation apparently failed, although I can use the program without problems. The real problem however is that every time I try to install something with Synaptic it stops halfway through to give me the message:

[I]A package failed to install. Trying to recover:
Setting  up netbeans5.5 (5.5-0.59)...

This package is an installer package, it does not actually contain
the netbeans IDE.        You will need to go download the IDE from:

[www.blabla.com/andsuch](www.blabla.com/andsuch)

and place the file in /tmp with root.root ownership now. 

[/I]

I tried downloading the IDE and placing it in /tmp, but to no avail. 

What to do?

---

### Post by ukripper on 2007-09-21
Go to synaptic and mark it for reinstallation. This way it will get rid of any broken dependencies causing it to fail.

---

