---
title: "How do I stop File Browser and Sessions Manager from loading on startup?"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by Charco on 2006-11-12
I have a strange problem where the file brower and session browser loads on startup! Thanks in advance for your help!

[[img=http://img354.imageshack.us/img354/4053/screenshot2wm8.th.png]](http://img354.imageshack.us/my.php?image=screenshot2wm8.png)

Update:
Ok so I did some digging and found out it was becuase my session was saved like that. So I ran:
gnome-session-save with nothing opened.
My problem now is that terminal starts up everytime! How do I fix this?

---

### Post by hopstah on 2006-11-12
i'm guessing you ran gnome-session-save from a terminal, am i right?  well, hit alt+f2 to bring up a run dialog, and run gnome-session-save from that instead.

---

### Post by Charco on 2006-11-13
Thank you.

---

