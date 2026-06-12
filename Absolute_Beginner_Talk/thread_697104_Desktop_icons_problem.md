---
title: "Desktop icons problem"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by mad_max0204 on 2008-02-14
I have this strange problem. Since I restarted my computer all my desktop icons are now displayed as iconname.desktop and if I click on them text file opens ?!?!?
In the right click properties it says Type : plain text document, location is good, MIME type : text/plain.

How to fix this problem ??

---

### Post by Gen2ly on 2008-02-14
It looks like you removed gnome mime types.  I'm not exactly sure the name in the repos but it's probably close to this ;)

---

### Post by mad_max0204 on 2008-02-14
Once again I'm gonna reply to my own post :D

I just run sudo update-mime-database /usr/share/mime and restarted and it was all back to normal :D

---

