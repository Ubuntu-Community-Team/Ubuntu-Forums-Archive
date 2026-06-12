---
title: "cgwd toolbar missing"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by whoosh on 2006-09-05
So I got the whole cgwd themer to work, but whenever I start up X, the toolbars on my windwos won't show up.  I try to hold alt and drag the windows but that doesn't work either. I can't even switch workplaces...

I restart compiz, but nothing works.  I get the regular toolbar back when I switch to metacity.

Cgwd and compiz/xgl worked for like three days but now this happened.

Can anyone help me out?

---

### Post by whoosh on 2006-09-05
One thing I've noticed is that when I switch to metacity, and type in "thefuture" into console, everything else works fine.

---

### Post by chicken101 on 2006-09-05
This was caused by a pesky update the other day.  Now they are using a thing called csm to changed compiz settings, instead of gconf-editor.

go to system ->preferences -> sessions and go to the startup programs tab.

Delete the old way you started compiz, and then add a program called "/usr/bin/compiz-start" without the quotes.

then type "compiz-start" in your terminal or press ctrl +alt+delete to restart xgl.

:cool:

---

### Post by bazz on 2006-09-06
Awesome Fix!!!! That fixed my problem. For KDE all I did was copy the "compiz-start" file to my /home/user/.kde/Autostart, restarted X and every thing works. Good Find!!!

---

### Post by xmux on 2006-09-08
Hey Thaks, I tried everything and at the end i found this post thaks for the Help!!

and how is this csm working?

---

