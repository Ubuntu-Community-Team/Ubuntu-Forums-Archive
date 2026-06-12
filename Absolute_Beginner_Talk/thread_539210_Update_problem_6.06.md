---
title: "Update problem 6.06"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by jhg999 on 2007-08-30
After installing the distro a huge list of updates appeared. I selected to install the updates. About ten minutes into the updates the power was lost. I  can't restart updates. A message appears that a "system administrative task is starting", a busy activity icon appears and nothing happens. Same thing happens when I try  to check for updates. If you mouse over the "updates available icon" it indicates 260 updates availble.

How do I get the to install?

TIA

Jerry

---

### Post by ThrobbingBrain66 on 2007-08-30
Could you open a terminal (Applications > Accessories > Terminal) and then enter:
```
sudo dpkg --configure -a
```

Hopefully this will configure any updates that were partially installed.  Then you should be able to resume your updating.

---

### Post by jhg999 on 2007-08-30
Tried your suggestion. This is the reply message:

sudo: unable to lookup  via gethostbyname()

---

### Post by ThrobbingBrain66 on 2007-08-30
Currently you have bigger problems than not being able to install updates. :)  Try this thread:
[http://www.linuxquestions.org/questions/showthread.php?p=2406796](http://www.linuxquestions.org/questions/showthread.php?p=2406796)

---

### Post by jhg999 on 2007-08-31
TB66,

Thank you for all of your help.

I solved the problem by reinstalling Ubuntu.

JHG

---

### Post by ThrobbingBrain66 on 2007-08-31
That was going to be my next suggestion.  Since you had just installed it, it wouldn't have been too much of a pain to reinstall.  Glad everything is working now. :)

---

