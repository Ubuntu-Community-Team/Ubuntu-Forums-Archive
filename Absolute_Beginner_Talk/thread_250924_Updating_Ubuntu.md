---
title: "Updating Ubuntu"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by qwazert on 2006-09-04
I am currently running a fully-functional (albeit older) version of Ubuntu...5.10 I believe...with KDE.
I also downloaded and tried out the NEWEST version (6.06) and it looks interesting. 

My question is: If I decide to UPDATE to this newest version, will it mean deleting the older version entirely, will I lose all my settings, bookmarks, addresses, and other applications?

Something I need to know before I commit to an upgrade...no sense fixing something that already works, right?


Thanks to all who answer my many questions!:-D

---

### Post by zxee on 2006-09-04
Barring any problems your settings shouldn't be at all affected by an upgrade. Settings are usually in your home directory and the same for installed software-although it depends on how it was installed. If your added software was installed through apt-get or one of the gui package mangers based on it then you should be fine there too.
Some people like to use synaptic or in kde adept for upgrading. You could check out the man i.e > man apt-get

---

### Post by Jussi Kukkonen on 2006-09-04
> no sense fixing something that already works, right?
True. If you have no problems, you might not want to upgrade -- 5.10 will get security updates at least to next spring.

> My question is: If I decide to UPDATE to this newest version, will it mean deleting the older version entirely, will I lose all my settings, bookmarks, addresses, and other applications?
Oh no. The upgrade process is mostly very easy and you definitely won't lose your data. A bit trickier upgrade situations should be expected if you have done a lot of configuration changes -- editing config files by hand and so on.

---

### Post by tkiesel on 2006-09-04
Hi qwazert,

You should just need to run Update Manager with the -d option to start the process of upgrading to Dapper.


Type the following in a terminal. (and leave the terminal open for the whole procedure)

```
gksudo update-manager -d
```

Good ol update manager should take you through the whole process of upgrading to Dapper like a champ. :)

You won't lose your personal settings.  The machine I'm typing this on now started with Warty (Ubuntu 4.10). I've upgraded it to new Ubuntu versions three times now and am looking forward to going ahead into Edgy with it. :)

Much love,
-T

---

### Post by qwazert on 2006-09-04
Allright TK, I'll try your suggestion and see what happens...

---

### Post by qwazert on 2006-09-04
Hmmmm...Update Manager says that it will take "several hours" to upgrade....746Megs of stuff to download!

This will have to be done late at night, I'll post results tomorrow.

---

