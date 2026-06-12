---
title: "xorg.conf major problem"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by Gorgazm on 2006-03-29
Ok, well the problem started when I needed to fix the alignment of my screen due to the fact that it was off to the left a little too much, I made the corrections in the xorg.conf file saved and restarted to check and see if it worked, well now X wont start because of a typo of some sort in the xorg.conf file.  So is there a way to edit xorg.conf file or replace with a new one?

---

### Post by Perfect Storm on 2006-03-29
```

sudo nano /etc/X11/xorg.conf

```

---

### Post by Gorgazm on 2006-03-29
thanks a bunch, also got me screen centered :)

---

### Post by frodon on 2006-03-29
To edit your xorg.conf in terminal : ```
sudo nano /etc/X11/xorg.conf
```To replace it : ```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

### Post by meborc on 2006-03-29
[QUOTE=frodon]```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```[/QUOTE]

well... sometimes people don't have backups of xorg... i was one of them... i never back up... :mrgreen: i guess i will get burned because of it soon, but i really dont care...

anyways.. my point is that this command helps only if a xorg.conf.backup exists

---

