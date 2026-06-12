---
title: "Really weird Problem when I log into desktop!"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by zxcvbnm on 2006-07-18
I just installed the fglrx driver but when I log into desktop I can't move anywindow...For example I can't move terminal to the center of the screen or change to a different workspace.....There isn't even any "X"s on the windows so I can't close the window.....I went back to Vesa driver but It is still like that.

Right now I 'm on Failsafe Gnome session.....And it's working fine on this session

---

### Post by zxcvbnm on 2006-07-19
^^^^Bump^^^^^

---

### Post by falcon15500 on 2006-07-19
Have you been playing with Xgl/Compiz? This is a common occurrence when trying to get XLG/Compiz up and running correctly.

falc

---

### Post by zxcvbnm on 2006-07-19
Oh yea ...I did....I was trying to get it to work but I couldn't.....How would I uninstall it?

---

### Post by falcon15500 on 2006-07-19
Really depends on which, of the various methods, you were using to try to get it running.  If you got to the part where your window boxes are missing the title bars, you were very close to having it all up and working!  It might be easier to move ahead, rather than move backwards.
  Go into gconf, applications, compiz and see what plugins are listed for it.  You might have to add the plugins to get it all to work - the window decoration onein particular, I think.  I am not at my linux box presently, so I can't give you concrete directions.  There are plenty of threads on Xgl/Compiz, so you should be able to get pointers there.
  Failing that... Can you tell us what is listed in your sessions configuration, under startup programs?  Most Xgl/Compiz threads will use this area to actually start the "replace" operation.

falc

ps:  Sorry this is so vague!  Bascially, Xgl/Compiz is working for you - which is why the title bars are gone. The configuration for Compiz needs to be updated, so it will use the correct plugins - which includes one that will give you your title bars back. ;)

---

