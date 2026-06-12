---
title: "[SOLVED] sudo apt-get problem???"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by jorki on 2007-11-25
sudo apt-get install wine 

it shows the following error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wine


What should I do to fix it?

Thank you.

---

### Post by aysiu on 2007-11-25
Make sure you [have extra repositories enabled](http://www.psychocats.net/ubuntu/sources), then try again: ```
sudo apt-get update
sudo apt-get install wine
```

---

### Post by jorki on 2007-11-25
a big thanks for the advice
everything is OK after I enabled repositories

thank you ;)

---

