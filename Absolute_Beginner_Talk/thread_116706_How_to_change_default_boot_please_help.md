---
title: "How to change default boot? please help"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by madu on 2006-01-13
Hi guys..

I want to know how I can change the default boot OS to windows in GRUB.
I looked at Tips&Tricks and changed the default 0 to X_sequence, but didnt make in different..
What does exactly X_sequence do? I didnt find any X_sequence words in that file anywhere..?
How does it load Windows by default with X_sequence..
Please help guys.. Thanks!

---

### Post by aysiu on 2006-01-13
X_Sequence is imprecise. You want to change 0 to another number. For example, a typical grub order looks like this:

0 Ubuntu
1 Ubuntu recovery
2 Memtest
3 Other operating systems descriptor
4 Windows XP

So if you wanted to change the default from Ubuntu to Windows, you'd change ```
default 0
``` to be ```
default 4
```

---

### Post by madu on 2006-01-13
thanks aysiu..

that makes sense..will try that..
Thanks a lot,,!

---

