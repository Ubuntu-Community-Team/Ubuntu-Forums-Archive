---
title: "3 Quick Questions."
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by Chake99 on 2007-01-20
Yes. Or so I hope. 

How do I open a program from the command line but have the command line stay active? I've installed Kuake, which I love and have been using it to launch some programs more often than the GUI menu, but until the program is closed it is inactive.

How do I unpack multiple .deb files that I downloaded that are all dependant on each other?

How do I unlock a passworded .rar with ark?

Thanks in advance.

---

### Post by Iarwain ben-adar on 2007-01-20
Hi there,

1) add an & after the command, like this:
```
kuake &
```

2)```
sudo dpkg -i *.deb
```
(do this when you are in the folder that contains your downloaded deb's, and only those deb's)

3) Don't know about that one, sorry


Iarwain

---

### Post by xpod on 2007-01-20
Not sure about the latter 2 but you can open a new tab in the terminal.

---

### Post by meng on 2007-01-20
3. Try opening the rar with Ark, then go Edit > Password.

---

