---
title: "Why can't I install anything?"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by PerfectD3 on 2008-01-27
Seems whenever I try to download anything, upgrade, or get updates I keep getting the same old message and it won't let me finish.  Here's the message, and yes I am completely linux stupid.  Taking the linux challenge right now


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by overdrank on 2008-01-27
> **PerfectD3 said:**
> Seems whenever I try to download anything, upgrade, or get updates I keep getting the same old message and it won't let me finish.  Here's the message, and yes I am completely linux stupid.  Taking the linux challenge right now


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

HI and welcome, you need to run that command ```
sudo dpkg --configure -a
``` in the terminal located under applications, accessories.

---

### Post by Majorix on 2008-01-27
Run Applications > Accessories > Terminal.

Enter "sudo dpkg --configure -a" in there.

EDIT: Lol I was too slow.

---

### Post by taurus on 2008-01-27
If you have synaptic or Add/Remove open, close it.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by PerfectD3 on 2008-01-27
Lol thanks guys, I was thinking it was more complicated than that.

---

