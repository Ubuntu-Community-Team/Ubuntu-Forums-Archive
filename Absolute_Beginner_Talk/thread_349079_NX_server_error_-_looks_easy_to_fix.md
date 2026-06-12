---
title: "NX server error - looks easy to fix?"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by yezzer on 2007-01-29
Hi!

i've got NXserver running OK on a machine of mine- everything works on my LAN!

The only problem is when i connect from outside my lan.. SSH works ok, but im having problems with NX..
I've found what look like EXACTLY my problem - and solution here:
[http://www.linuxquestions.org/questions/showthread.php?t=510837]("http://www.linuxquestions.org/questions/showthread.php?t=510837")

Specifically Linux_junky has the same error which is solved by this command:

> fc-cache -fv
/sbin/conf.d/SuSEconfig.fonts

cd /usr/X11R6/lib/X11/
rm -Rf fonts/
ln -s /usr/share/fonts .

fc-cache -fv
/sbin/conf.d/SuSEconfig.fonts

My question is, what is the equivalent of those commands? Im running edgy.. 

TIA! :)

---

### Post by yezzer on 2007-01-30
Sorry to bump this.

I can connect OK on other windows machines outside my LAN - it's just one specific windows machine that's causing this problem

any ideas?

---

