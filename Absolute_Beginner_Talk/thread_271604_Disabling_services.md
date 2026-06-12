---
title: "Disabling services"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by crokett on 2006-10-04
How to disable services in Ubuntu?  The gui app under administration doesn't list them all.  I also don't see the usual /etc/rc.d/rcX.d directory structure to modify the runlevels.  Specifically I want to start by disabling bluetooth and bittorrent, neither of which I ever use.

---

### Post by bodhi.zazen on 2006-10-04
This is comprehensive:

[Ubuntu speed Boot](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by aysiu on 2006-10-04
It can be quite a bit simpler than that, actually.

Step 1: [http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories](http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories)

Step 2: ```
sudo aptitude update
sudo aptitude install bum gksu
gksudo bum
```

Step 3: Uncheck whatever services you don't need.

---

### Post by crokett on 2006-10-04
kewl.  thanks.  i;m dumb - was looking in the wrong place for the runlevel directories...

---

