---
title: "Firefox problem - can't find an archieve for it"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by Sef on 2006-04-17
While installing libstdc++5, I got this problem:

> sef@joker1:~$ sudo apt-get install libstdc++5
Password:
Reading package lists... Done
Building dependency tree... Done
E: The package firefox-1.5 needs to be reinstalled, but I can't find an archive for it.


What does this mean? What should I do?

---

### Post by christhemonkey on 2006-04-17
If you installed an updated firefox from source, then apt may be looking for it in the repositories, so cant find it.
Try removing firefox installing libstdc++5, and then reinstalling firefox.

---

### Post by Sef on 2006-04-17
I did try to update firefox, but up came a message saying it had failed.  Guess it had gotten partially installed. Oh well.  Now to figure out how remove it.  I think it is on the wiki.

---

