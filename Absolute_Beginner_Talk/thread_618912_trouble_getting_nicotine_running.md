---
title: "trouble getting nicotine running"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by xboxbman on 2007-11-20
i've been trying to run nicotine for some time, but it won't work, all i get is a blank window.  when i try to run it from terminal i get this : ```
Nicotine supports "psyco", an inline optimizer for python
code, you can get it at http://sourceforge.net/projects/psyco/
Nicotine supports a country code blocker but that
requires a (GPL'ed) library called GeoIP. You can find it here:
C library:       http://www.maxmind.com/app/c
Python bindings: http://www.maxmind.com/app/python
(the python bindings require the C library)

Traceback (most recent call last):
  File "/usr/bin/nicotine", line 155, in <module>
    app = frame.MainApp(config, trayicon)
  File "/var/lib/python-support/python2.5/pynicotine/gtkgui/frame.py", line 1666, in __init__
    self.frame = testwin(config, trayicon)
  File "/var/lib/python-support/python2.5/pynicotine/gtkgui/frame.py", line 396, in __init__
    if self.np.config.needConfig():
  File "/var/lib/python-support/python2.5/pynicotine/config.py", line 87, in needConfig
    if self.sections[i][j] is None or self.sections[i][j] == '' and i not in ("userinfo", "ui", "ticker", "players") and j not in ("incompletedir", "autoreply", 'afterfinish','afterfolder', 'geoblockcc'):
  File "/usr/lib/python2.5/UserDict.py", line 173, in __cmp__
    return cmp(dict(self.iteritems()), other)
  File "/usr/lib/python2.5/UserDict.py", line 105, in iteritems
    for k in self:
  File "/usr/lib/python2.5/UserDict.py", line 92, in __iter__
    for k in self.keys():
  File "/usr/lib/python2.5/shelve.py", line 92, in keys
    return self.dict.keys()
  File "bsddb/__init__.py", line 252, in keys
  File "bsddb/dbutils.py", line 62, in DeadlockWrap
bsddb.db.DBPageNotFoundError: (-30987, 'DB_PAGE_NOTFOUND: Requested page not found')


```

any ideas?  I'm sure it's something simple, but it's beyond me.  Oh, and I'm running feisty.

---

### Post by xboxbman on 2007-11-20
hey, i fixed it myself just like a big boy.  Just had to remove all the .db files in my /.nicotine dir.  soooo, anyone else having this problem, that's how you fix it.

---

### Post by Crazy Jesus on 2008-02-01
Thanks for posting your solution, it worked a treat for me! :)

---

### Post by jan quark on 2008-02-01
pls mark this thread as solved to help other users find the solution quicker

you can do this using the thread tools
thank you

---

### Post by OscarGortez on 2008-02-04
Props to posted the fix on your own question... it actually fixed the issue I was having with nicotine as well...

---

