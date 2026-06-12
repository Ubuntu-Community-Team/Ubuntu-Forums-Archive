---
title: "Use ndiswrapper"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by Loki1989 on 2006-07-14
how do you run it after you get it installed

---

### Post by Jagot on 2006-07-14
Get the Windows driver for your card (mine happens to be bcmwl5.inf) then it goes something like this:

```
sudo ndiswrapper -i ~/Desktop/bcmwl5/bcmwl5.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```

Then it should be a matter of configuring the connection in Administration -> Networking.

---

