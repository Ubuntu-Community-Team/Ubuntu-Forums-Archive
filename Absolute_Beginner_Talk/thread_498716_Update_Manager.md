---
title: "Update Manager"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Adaminla on 2007-07-11
I got a notice this AM when I loged in that there were 18 updates ready but when I tried to use the manager I got a message that the updates were not authenticated and that my machine couldn't fetch the updates.  What's going on? Is this a problem with my PC or is this a roblem at the server?

---

### Post by taurus on 2007-07-11
Close that update window if you have it open.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude upgrade
```
Post the complete error message here if there is one.

---

### Post by mendingo84 on 2007-07-11
server problem ;). i had the same problem today, but now everything is working fine. do you happen to be from Romania?

---

### Post by Adaminla on 2007-07-11
thanx, mandingo, No I'm not Romanian. USA.

---

### Post by Adaminla on 2007-07-11
Thanx, Taurus. I went to terminal and download and update/upgrade went smooth as silk.Was it just to much for update manager to handle? I'm still new to the whole linux scene. Learning all the time.

---

