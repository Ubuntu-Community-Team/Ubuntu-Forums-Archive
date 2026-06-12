---
title: "Feisty and config files"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by AlanD on 2007-04-16
I have a question about updating to feisty - i had to do a lot of trickery in order to get my wifi (bwcutter i think it was called), sleep/hibernation (through editing xorg.conf) and partition mountings to work properly. If I do an update to feisty, will I lose these changes?

---

### Post by Happy_Man on 2007-04-16
Not if you go into /etc/apt/sources.list and change all instances of "dapper" or "edgy" to "feisty." Then open up a terminal and enter

```

sudo apt-get dist-upgrade

```

Hope this helps!

---

### Post by rsambuca on 2007-04-16
> **Happy_Man said:**
> Not if you go into /etc/apt/sources.list and change all instances of "dapper" or "edgy" to "feisty." Then open up a terminal and enter

```

sudo apt-get dist-upgrade

```

Hope this helps!Actually, it is not recommended to upgrade via this method.

Rather, you should```
gksu "update-manager -c" 
```You'll have to wait until the official version is released for this.  If you are too impatient to wait 3 more days, you can use gksu "update-manager -c-d"

---

