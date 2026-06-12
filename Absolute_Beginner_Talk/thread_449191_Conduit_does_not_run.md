---
title: "Conduit does not run"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-05-20
I tried to run conduit in Kubuntu Feisty but it crashes.

I ran it in the terminal to see the error report and here it is
```
user@laptop:~$ /usr/bin/start_conduit
Traceback (most recent call last):
  File "/usr/bin/start_conduit", line 26, in <module>
    import conduit
  File "/usr/lib/python2.5/site-packages/conduit/__init__.py", line 127, in <module>
    import Settings
  File "/usr/lib/python2.5/site-packages/conduit/Settings.py", line 12, in <module>
    import gconf
ImportError: No module named gconf
user@laptop:~$ /usr/bin/start_conduit
Traceback (most recent call last):
  File "/usr/bin/start_conduit", line 26, in <module>
    import conduit
  File "/usr/lib/python2.5/site-packages/conduit/__init__.py", line 127, in <module>
    import Settings
  File "/usr/lib/python2.5/site-packages/conduit/Settings.py", line 12, in <module>
    import gconf
ImportError: No module named gconf

```

How do I run conduit?

---

