---
title: "Having problems installing qbittorrent..."
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by iamiso on 2007-07-14
This could be VERY duh! but here goes.

I'm trying to install qbittorrent on feisty as described on other threads and I need to add the following to my sources list.....

deb [http://hydr0g3n.free.fr/qbittorrent/feisty/](http://hydr0g3n.free.fr/qbittorrent/feisty/) ./
deb-src [http://hydr0g3n.free.fr/qbittorrent/feisty/](http://hydr0g3n.free.fr/qbittorrent/feisty/) ./

however when I pull up my list (as root) it will not let me edit it so I can add those 2 lines! What HUGE basic mistake am I making? 

Any help appreciated...

---

### Post by mevets on 2007-07-14
Are you running the cmd
```

sudo gedit /etc/apt/sources.list

```
?

---

### Post by iamiso on 2007-07-15
Perfect - thank you! I was running a slightly incorrect command!

---

