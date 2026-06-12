---
title: "Xubuntu: Local wireless network search?"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by leo7068 on 2007-06-01
Does Xubuntu have a wireless network search function? I forgot the name of my SSEID and couldn't search for available wireless networks, so was unable to get internet. My temporary solution was to install Ubuntu, but I really prefer the quicker simpler Xubuntu.

---

### Post by jd65pl on 2007-06-01
Try

```
iwlist scan
```

---

### Post by leo7068 on 2007-06-01
Great, thanks for the code. So now that I know how to list available wireless networks I would assume I just put the listed SSEID into the GUI Wireless setup. 

Is there a way of storing more than 1 wireless network, so it will go to the other if the first goes down/looses signal?

---

### Post by ugm6hr on 2007-06-01
Or you could just add Network Manager to Xubuntu:

[http://ubuntuforums.org/showthread.php?t=448952](http://ubuntuforums.org/showthread.php?t=448952)

PS: Network Manager is the auto-search wireless facility in Ubuntu.

---

### Post by kernel tom on 2007-06-01
> **leo7068 said:**
> Great, thanks for the code. So now that I know how to list available wireless networks I would assume I just put the listed SSEID into the GUI Wireless setup. 

Is there a way of storing more than 1 wireless network, so it will go to the other if the first goes down/looses signal?

i use wlassistant it's amazing

sudo apt-get install wlassistant

then run it as root

sudo wlassistant

brings up all availible networks, stores WEP's and settings, and connects you

---

