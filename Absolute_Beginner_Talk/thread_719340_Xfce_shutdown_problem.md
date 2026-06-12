---
title: "Xfce shutdown problem"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by gvhg on 2008-03-09
I've folloed the instrusctions in [http://wiki.xfce.org/faq?s=dependencies#session_manager](http://wiki.xfce.org/faq?s=dependencies#session_manager)

But the thing is that I do not have this xfsm-shutdown-helper file, so I am lost as to what to do.

Any help there? Thanks.

---

### Post by banewman on 2008-03-09
Can you let us know why you need to go to this amount of effort?
You don't have the normal quit entry in the menu?
sudo shutdown -h now
in a terminal is another way.
Knowing the different way you are using the os will help. 
If you have something like the normal ubuntu with xfce also installed then going the visudo root and adding the line
(you're username) ALL = NOPASSWD: /usr/sbin/shutdown
then making a shortcut which has the command
sudo shutdown -h now
will give you one click shutdown
:)

---

