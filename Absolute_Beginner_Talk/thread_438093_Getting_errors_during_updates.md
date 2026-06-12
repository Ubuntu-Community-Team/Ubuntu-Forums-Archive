---
title: "Getting errors during updates"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Keitarosan on 2007-05-09
Hey there, I'm having a problem with the automatic updates, when I try to update it says
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I've only had Linux for like 2 days, so I'm not really sure what to do. Thanks.

---

### Post by Thingymebob on 2007-05-09
open a terminal
Applcations > Accessories > Terminal
Type
 sudo dpkg --configure -a

the password you are asked for should be your login password.

---

### Post by Keitarosan on 2007-05-09
Thank you very much, it's working now

---

### Post by David4 on 2007-05-16
Hi
am getting the same? error
typed
sudo -dpkg -configure -a
and get this error
sudo: please use single character options
sudo: illegal option `-dpkg'
Not sure what I am doing wrong
thanks 
David

---

### Post by taurus on 2007-05-16
It's

```
sudo dpkg **--**configure -a
```

---

### Post by David4 on 2007-05-16
Taurus
thank you very much
I was miss typing the command
thank you 
David

---

