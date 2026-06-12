---
title: "Removing queued package installs"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by Enigmatic on 2006-06-03
I tried installing Cacti, but I don't think I had Mysql configured so it never finished.

Now, whenever I try to add a package, it tries to finish Cacti's installation, and since it can't the other package doesn't seem to get added.

Is there any way I can remove Cacti from the "queue"?

---

### Post by catlett on 2006-06-03
Aptitude deals with stuff like this well. You can try a few different things and one of them should work. ```
sudo aptitude remove cacti
``` ```
sudo aptitude upgrade
``` or the next time you install something use aptitude and it will deal with cacti ```
sudo aptitude install something
```
Aptitude is doing the same thing as apt-get. They are just 2 different front ends to the repositories and the apt package system.

---

