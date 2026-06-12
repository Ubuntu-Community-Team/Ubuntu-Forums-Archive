---
title: "Module odbchelper"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by resistantgnome on 2007-06-29
I was reading ***Dive Into Python***. Tried one example of it which imports odbchelper but it gave the following error

> >>> import odbchelper
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
ImportError: No module named odbchelper


I looked into all the path manually but could not find .py file corresponding to it. Here's the sys.path output 
> >>> import sys
>>> sys.path
['', '/usr/lib/python24.zip', '/usr/lib/python2.4', '/usr/lib/python2.4/plat-linux2', '/usr/lib/python2.4/lib-tk', '/usr/lib/python2.4/lib-dynload', '/usr/local/lib/python2.4/site-packages', '/usr/lib/python2.4/site-packages', '/usr/lib/python2.4/site-packages/HTMLgen', '/usr/lib/python2.4/site-packages/Numeric', '/usr/lib/python2.4/site-packages/PIL', '/usr/lib/python2.4/site-packages/gtk-2.0', '/usr/lib/site-python']

Where can I download that module?

---

### Post by jfinkels on 2007-06-29
> **resistantgnome said:**
> I was reading ***Dive Into Python***. Tried one example of it which imports odbchelper but it gave the following error




I looked into all the path manually but could not find .py file corresponding to it. Here's the sys.path output 


Where can I download that module?

Take a look at Section 2.1, Example 2.1, here: [http://www.diveintopython.org/getting_to_know_python/index.html](http://www.diveintopython.org/getting_to_know_python/index.html)

That code IS odbchelper. You can download it with the link he gives.

---

