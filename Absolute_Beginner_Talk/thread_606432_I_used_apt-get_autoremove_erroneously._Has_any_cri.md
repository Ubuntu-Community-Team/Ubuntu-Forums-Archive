---
title: "I used apt-get autoremove erroneously. Has any critical package gone(see small list)?"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by offline on 2007-11-07
Using 

```
apt-get autoremove 
```

some or all of  these files(i checked **dpkg log** since I haven't found any apt-get log) were removed. Can you say if any of them is of critical importance so that I should reinstall?

```
g-wrap 1.9.6-3.1ubuntu1 1.9.6-3.1ubuntu1
libgwrap-runtime0-dev 1.9.6-3.1ubuntu1 1.9.6-3.1ubuntu1
guile-1.6-dev 1.6.8-6build1 1.6.8-6build1
guile-g-wrap 1.9.6-3.1ubuntu1 1.9.6-3.1ubuntu1
guile-library 0.1.2-1 0.1.2-1
libgwrap-runtime0 1.9.6-3.1ubuntu1 1.9.6-3.1ubuntu1
libffi4-dev 4.1.2-0ubuntu4 4.1.2-0ubuntu4
libffi4 4.1.2-0ubuntu4 4.1.2-0ubuntu4
libgsf-gnome-1-114 1.14.3-1ubuntu2 1.14.3-1ubuntu2
libreadline5-dev 5.2-2ubuntu1 5.2-2ubuntu1
libncurses5-dev 5.5-5ubuntu2 5.5-5ubuntu2
```

Thanks.

---

### Post by ubnewbie2 on 2007-11-07
No, everything should be fine.  They were packages that should no longer be required for the software you have installed.

---

