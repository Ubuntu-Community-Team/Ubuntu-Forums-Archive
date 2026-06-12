---
title: "Stupid copy question"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by Tadhg on 2006-07-30
Im almost embarresed asking this, but i want to back up my Home directory completely by copying everything to an external drive, but i have 17gb of music there which i want to be excluded. How should i do this? I've been trying;

sudo cp -R [!music]* /home/timmy /media/drive

What am i doing (stupidly) wrong?

---

### Post by trent dillman on 2006-07-30
...

---

### Post by adamkane on 2006-07-30
You probably need to use tar with -exclude:
[http://www.linuxforums.org/forum/linux-programming-scripting/64310-copy-everthing-except.html](http://www.linuxforums.org/forum/linux-programming-scripting/64310-copy-everthing-except.html)

Try sbackup (a GUI for tar), if you have trouble with tar.

---

