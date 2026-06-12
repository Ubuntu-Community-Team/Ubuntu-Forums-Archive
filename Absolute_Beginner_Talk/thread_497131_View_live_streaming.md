---
title: "View live streaming"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by fongs on 2007-07-09
Is it possible on linux (ubuntu) to view windows media type File live steaming. If so on what applications.

---

### Post by lbelloq on 2007-07-09
Try mplayer + w32codecs.

---

### Post by fongs on 2007-07-09
> **lbelloq said:**
> Try mplayer + w32codecs.

how and where do i find the codecs and also how do i install them.
Thanks for help.

---

### Post by lbelloq on 2007-07-09
IIRC:

sudo apt-get install mplayer * w32codecs

---

### Post by fongs on 2007-07-09
> **lbelloq said:**
> IIRC:

sudo apt-get install mplayer * w32codecs

Doesn't seem to work 
```
fongs@fongs-desktop:~$ sudo apt-get install mplayer * w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mplayer is already the newest version.
E: Couldn't find package Desktop
```

---

### Post by lbelloq on 2007-07-09
Then try:

sudo apt-get install w32codecs

---

### Post by fongs on 2007-07-09
> **lbelloq said:**
> Then try:

sudo apt-get install w32codecs

```
fongs@fongs-desktop:~$ sudo apt-get install w32codecs
[sudo] password for fongs:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

```

what does this mean.

---

### Post by fongs on 2007-07-28
Please help I'm having trouble and can't seem to view any type of live streaming video that i would normally view on windows media player. any thought s are greatly appreciated.

---

