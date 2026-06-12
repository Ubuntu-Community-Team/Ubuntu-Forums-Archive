---
title: "dpkg --configure -a'"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by joselon on 2008-01-07
Hello. This is my first time with Ubuntu and my first time on a Forum.  I keep getting this message everytime I try to install or update anything. I have Ubuntu 7.10 the Gutsy Gibbon.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Thanks

---

### Post by p_quarles on 2008-01-07
Well, you can always try doing what it says. ;) In a terminal, type:
```
sudo dpkg --configure -a
```

---

### Post by ryanVickers on 2008-01-07
looks like you should run ```
dpkg --configure -a
``` in the terminal (applications > accessories) to correct the problem ;)

---

### Post by bwtranch on 2008-01-07
That may not work, though. dpkg has a bug in it. Unless it has been fixed you have to run (as root) sudo gedit /var/lib/dpkg/status

Look at the file entries and you will see something like the file failed or halfway installed etc. Delete that entry and save. Now, go to Synaptic and completely delete the offending package. This is a hack workaround, but until that bug is fixed, I don't know any other way.

---

### Post by doorknob60 on 2008-01-07
That happened to me when I tried to install the Flash Player, which doesn't install correctly and i fixed it by doing [```
sudo dpkg --configure -a
``` and it worked fine after that.

---

### Post by ryanVickers on 2008-01-07
wow we're not redundant or anything... :rolleyes:

---

