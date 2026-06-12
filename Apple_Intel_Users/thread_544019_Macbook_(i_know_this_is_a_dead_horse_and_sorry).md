---
title: "Macbook (i know this is a dead horse and sorry)"
date: 2007-09-05
forum: Apple Intel Users
---

### Post by backinthecity on 2007-09-05
I'm currently trying to get my intel 950 working at full resolution but for some reason I'm only running at 1024x768 ... Just quick question
How do you install at a "service level"? 
what is a "service level" ?


thanks a head of time for the help-
-drake

---

### Post by benanzo on 2007-09-06
If you're using the "i810" driver (which you probably are) do:
```
sudo apt-get install 915resolution
```
then reboot.  You could also install the "intel" driver.

---

