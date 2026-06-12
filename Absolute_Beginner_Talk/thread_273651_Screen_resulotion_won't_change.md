---
title: "Screen resulotion won't change"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by fontenot_1031 on 2006-10-08
Some how my screen resolution is stuck at 642 x 424 or something like that.  I can't change it back to it's previous state, I think it was 1024 x 768.  The drop down menu only has 1 option, the current one.  Anway it's really annoying because I can't see all of certain windows.

---

### Post by jd65pl on 2006-10-08
You may like to try the command below to reconfigure your xserver, make sure you have the correct drive selected.

```
sudo dpkg-reconfigure xserver-xorg
```

---

