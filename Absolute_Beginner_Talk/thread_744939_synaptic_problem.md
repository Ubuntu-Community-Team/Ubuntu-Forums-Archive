---
title: "synaptic problem"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by harry rao on 2008-04-04
i'm having an issue, whenever i'm opening synaptic or try and run any sudo commands i get the following issue:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

could someone please provide the solution?

---

### Post by kellemes on 2008-04-04
> **harry rao said:**
> i'm having an issue, whenever i'm opening synaptic or try and run any sudo commands i get the following issue:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

could someone please provide the solution?

Open a terminal-window and start typing..
```
sudo dpkg --configure -a
```

---

### Post by harry rao on 2008-04-04
well i did it before and i just thought it was taking too long, i was a bit more patient and it worked.

---

### Post by harry rao on 2008-04-04
i have wine.
can someone please tell me how i can run a .exe file?

-harry.

---

### Post by paydaydaddy on 2008-04-04
Right click on the file and choose "open with" from the drop down menu, then choose wine. Been a while since I did this, but I know that it is close enough to how it works that you will figure it out. After choosing "open with wine" you pretty much just let it do it's thing and it will either work, or it won't. Wine works for a lot, but not everything.

---

