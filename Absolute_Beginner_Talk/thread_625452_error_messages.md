---
title: "error messages"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by Dannyblueyes on 2007-11-28
I have Ubuntu Gutsy. Every time I try to install or uninstall a program from the application menu I get the following error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

This problem just occurred recently, after a botched install of Kaffine. While installing I was prompted to insert the install disc. In the middle the computer froze up. I restated the system forgetting to remove the install disc first. I immediately removed the disc, and restarted the system a second time. 

Before this the application install/uninstall worked seamlessly 

Is there any way to fix this blunder or do I have to completely re-install the system?

---

### Post by PmDematagoda on 2007-11-28
Why don't you try:-
```

sudo dpkg --configure -a
```
in a terminal and see if that would solve your problem.

---

### Post by Dannyblueyes on 2007-11-28
That seems to have worked. Thank you very much for your help.

---

