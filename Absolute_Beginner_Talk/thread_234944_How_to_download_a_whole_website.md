---
title: "How to download a whole website"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by Bloch on 2006-08-12
I want to download a whole website for offline use. The POlish python doc site in fact. I need to download just one link deep, obviously not infinitely deep!!
[http://www.python.org.pl/](http://www.python.org.pl/)

What's the best solution?
Bloch

---

### Post by jordilin on 2006-08-12
Just type:
```
wget -r -l0 --no-parent http://urltodownload
```

---

### Post by Engnome on 2006-08-12
httrack, its in the repos.

---

### Post by Bloch on 2006-08-12
Thanks you guys;
wget did the trick - I'll look up httrack later.

Many thanks
Aiden

---

### Post by clarkth on 2006-08-12
> **Engnome said:**
> httrack, its in the repos.

OK, stupid question.  I just installed httrack but it is not in the menu.  How do I run it and how do I get it on the menu?  Thanks.

---

### Post by jordilin on 2006-08-12
> **clarkth said:**
> OK, stupid question.  I just installed httrack but it is not in the menu.  How do I run it and how do I get it on the menu?  Thanks.

Open a terminal and type its name
```
httrack &
```
followed by an intro.
To add it in the menu, go to Applications->Accessories->Alacarte's menu editor and see if you can add it from there.

---

### Post by clarkth on 2006-08-12
> **jordilin said:**
> Open a terminal and type its name
```
httrack &
```
followed by an intro.
To add it in the menu, go to Applications->Accessories->Alacarte's menu editor and see if you can add it from there.


Thanks, running from the terminal works fine.

---

