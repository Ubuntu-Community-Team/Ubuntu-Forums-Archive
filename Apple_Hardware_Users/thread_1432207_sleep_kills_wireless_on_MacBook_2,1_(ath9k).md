---
title: "sleep kills wireless on MacBook 2,1 (ath9k)"
date: 2010-03-17
forum: Apple Hardware Users
---

### Post by linuxopjemac on 2010-03-17
I don't know exactly since when, but putting my MacBook 2,1 with Karmic Koala installed on it into sleep, kills the wireless connection. After suspend I need to remove and reload the ath9k module. Does anyone know here what to do about this? Is there a way to fix this?

---

### Post by linuxopjemac on 2010-03-17
I sort of fixed it by making some hooks in /etc/pm/sleep.d and /etc/pm/power.d as root. In /etc/pm/sleep.d I created 20_ath9k with the following into it:
```
#!/bin/sh  
rmmod -f ath9k
```
I chmod +x this file to make it executable

I did a similar thing in /etc/pm/power.d/10_ath9k:
```
#!/bin/sh  
modprobe ath9k
```

If anyone has a more elegant way to do this, please let me know.

---

