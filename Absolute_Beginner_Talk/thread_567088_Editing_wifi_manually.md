---
title: "Editing wifi manually"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by dvdljns on 2007-10-04
I paid someone to load linux on my laptop. He did and it works, but the wireless card looks for his network. I need to go into the config file a manually change the settings. It will not change by the grapical interface. But I can not find the file. it has xubuntu on it. What do I look for and how do I do it.

---

### Post by jpeddicord on 2007-10-04
The correct file is probably /etc/network/interfaces .

To edit it, type the following in a terminal:

```
sudo nano /etc/network/interfaces
```

---

