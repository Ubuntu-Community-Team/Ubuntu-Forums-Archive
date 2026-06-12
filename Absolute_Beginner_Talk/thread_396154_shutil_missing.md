---
title: "shutil missing"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by ingo on 2007-03-29
Hi, 

I'm not sure what I've done, but whenever I do ```
sudo apt-get install -f
``` I gett horrid messages along the line of```
Setting up bug-buddy (2.16.0-0ubuntu2) ...
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 8, in <module>
    import sys,os,os.path,shutil,tempfile
ImportError: No module named shutil
dpkg: error processing bug-buddy (--configure):
 subprocess post-installation script returned error exit status 1
```
I searched for shutil in the forums, did a google, but no joy. Anybody out there knows to get it to work properly?

---

### Post by Ecthelion on 2007-03-29
Since you use the -f option I guess you have a broken package on your system...

Which package is it? (I'm not sure I can say it's bug-buddy... Could be that bug-buddy is called upon to solve the problem)

---

### Post by ingo on 2007-03-29
I'm not sure what did it, but it appears to be solved now. All it took was a number of > sudo dpkg --configure -afollowed by > sudo apt-get install -funtil the system shut up :) Many thanks for your reply!

---

