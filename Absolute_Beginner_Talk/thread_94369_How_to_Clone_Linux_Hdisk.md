---
title: "How to Clone Linux Hdisk???"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by Robroy11976 on 2005-11-23
Is there any way to close na linux OS??? I mean what would i clone the whole hdisk which has linux OS into another disc??? Sort of like Ghost in Windows.  I'm having problem with my current hdisk, so i want to transfer it to another drive without having to install all over again.

---

### Post by suRoot on 2005-11-23
dd is a wonderful tool for this sort of thing.  I'm sure there are any number of gui tools out there that will clone, but dd has always worked for me.  It does the job & you don't need to eat any more disk space by installing another app.

Depending upon your setup & what exactly you want to clone, you could possibly get away with a wholesale disk clone, something like:

```
sudo dd if=/dev/hda of=/dev/hdb
```

Assuming /dev/hda is your existing disk & /dev/hdb is the new disk you've put in the system.

This article goes in to a lot of detail & should be a big help:
[http://www.google.com/url?sa=U&start=2&q=http://www.rajeevnet.com/hacks_hints/os_clone/os_cloning.html&e=747]("http://www.google.com/url?sa=U&start=2&q=http://www.rajeevnet.com/hacks_hints/os_clone/os_cloning.html&e=747")

---

### Post by Robroy11976 on 2005-11-23
Thanks .. i'll sure could use that .... so dd is already pre-installed in linux??? Will copy the whole thing including the system files???

---

### Post by suRoot on 2005-11-23
dd is already on the system.  It will do a bit-for-bit copy from disk one to disk two.

---

### Post by redactech on 2005-11-23
dd is built in in any Linux distribution

if you want to know more about how it works type dd --help or man dd in the terminal

---

### Post by Robroy11976 on 2005-11-23
Thanks guys ... you've been a great help

---

