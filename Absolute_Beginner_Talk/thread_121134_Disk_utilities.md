---
title: "Disk utilities"
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by qwazert on 2006-01-24
Don't mean to be a Windoze cling-on, but does LINUX come with any sort of disk tools ie: Defrag, Scandisk, etc?

---

### Post by Perfect Storm on 2006-01-24
No, it's not necessarily. Linux don't use it. It handle things by its own.

---

### Post by bscbrit on 2006-01-24
Firstly, there is no need to defrag - it is simply not required.

For a 'scandisk' equivalent, look at 'man fsck' on the command line.  However, you will find that the system will automatically carry out a 'fsck' (file system check) every so often (perhaps every 24 boots or so).  Other than that, the need to carry out your own fsck is a rare thing indeed unless you are in the habit of switching off your computer without letting the system shut down for you.

---

