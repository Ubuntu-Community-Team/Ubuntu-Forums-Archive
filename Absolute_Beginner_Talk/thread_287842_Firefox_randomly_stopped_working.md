---
title: "Firefox randomly stopped working"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2006-10-29
I get the following when trying launch Firefox, this is strange since it has been working up to now..

/opt/firefox/firefox-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

---

### Post by wieman01 on 2006-10-29
Run this from a terminal:
> sudo apt-get install libstdc++5
That'll fix it.

---

### Post by tommy1987 on 2006-10-29
worked a treat, thanks

---

