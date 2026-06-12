---
title: "F-Spot Error message"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by mdrowe on 2007-04-18
Newly-installed Ubuntu 6.10 with F-Spot gives error message for any action on photo: 
Received exception, "Object reference not set to an object."  Unable to save photo name.jpg.  Also, F-Spot is stuck on one photo and can't find others by browsing.  What am I doing wrong?

---

### Post by kpkeerthi on 2007-04-18
sudo aptitude purge fspot

And remove .fspot (if any) from your home folder. Get the latest version from [www.getdeb.net](www.getdeb.net) and see if that fixes the problem

---

