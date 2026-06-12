---
title: "Cmd Line System Info"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by cAllison on 2007-07-30
Is there any way to view system information (Avail Memory/CPU Status/etc) from the command line? (for Ubuntu Server)

---

### Post by Rocket2DMn on 2007-07-30
"top" might be the command you are looking for.
check the man page for further details on it.
```
man top
```
There are also commands to get snapshot info like temperatures or running processes.

---

### Post by AnRa on 2007-07-30
If you like top, yo should try [htop](http://packages.ubuntu.com/feisty/utils/htop)! ;)

---

### Post by pmg on 2007-07-31
The vmstat command shows a one line summary of system stats.   Run **vmstat 5** to show deltas every five seconds, or **vmstat 5 10** to stop after ten records.  It's less elaborate then **top**. but it's nice if you want a lines with deltas you can look at to see changes over time, or something to put into a file on a server to see changes over time.

---

