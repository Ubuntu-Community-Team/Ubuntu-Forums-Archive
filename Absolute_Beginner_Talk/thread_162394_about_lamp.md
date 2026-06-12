---
title: "about lamp"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by jackss on 2006-04-18
hi , i installed lamp recently but i want to uninstall it now
how can i do it?
thanks for any help

---

### Post by Sandlst on 2006-04-18
How did you install it?  From the repositories (search for it in syaptic, right click and mark for removal) from source (go to the folder with the makefile in it, where you did ./configure, make, and sudo make install- and type in a terminal) ```
sudo make uninstall
```  Post back if you installed it another way/have problems with the above two methods.

---

### Post by jackss on 2006-04-19
i installed by apt-get, how can i uninstall it

---

### Post by dickohead on 2006-04-19
sudo apt-get remove package-name

---

