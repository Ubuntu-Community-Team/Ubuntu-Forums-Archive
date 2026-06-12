---
title: "My window title bars have stopped showing, why?"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by inktri on 2008-01-02
My window title bars (bar with close, maximize, minimize, window title, and icon) disappeared, how can I restore them?

Thanks for the help

---

### Post by Saint Angeles on 2008-01-02
alt+f2... then type:

metacity --replace

---

### Post by WearZeeP on 2008-01-03
Also, if you use compiz-fusion with emerald, that would be 
```
emerald --replace
```
I too had this problem (with emerald) a while ago, and I used the emerald --replace alot, but then it would happen again, and again and again...
Then, I read somewhere, and I dont even know why it works, but I installed Xgl
```
sudo apt-get install Xgl
```
and restarted X (Ctrl+Alt+Backspace), and I have never had this problem again.

---

