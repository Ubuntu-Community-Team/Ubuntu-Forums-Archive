---
title: "wireless help please. i have the intel ipw2200"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by killjdead on 2007-02-18
hello everyone. good to be here. i am taking a linux class in school it is pretty good but it doesn't cover any newer features because the course is 4 years old. its linux basics i guess. I can't get my wireless card to work correctly, i don't even know where to start on this. i have looked at some guides but haven't had any luck on getting it to work. would someone mind helping a semi-noob on this one? thank you, i appreciate it. unfortunately i do not have any friends who are into computers, let alone linux so i have had to figure out everything on my own. i have figured out alot but not everything.:confused: 

mmnnddffcckkrr on AIM and [email]thecoolitguy@hotmail.com[/email] on msn messenger . it would be great if someone could walk me through this via IM

---

### Post by crispy_420 on 2007-02-19
I can't help you all the way but I can point you to a link I found:

[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

Hope that helps. The downside looks as though you'll have to compile it yourself.

---

### Post by pebo on 2007-02-19
The ipw2200 driver should work out of the box - at least it does on edgy. Try ```
sudo lsmod | grep ipw2200
``` to see if the driver is loaded. If it doesn't show up try ```
sudo modprobe ipw2200
```HTH

---

