---
title: "Nicotine+ Keeps Crashing."
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by jarvis13 on 2007-05-22
It won't even start up. I just get the window border and inside is all blank.
It was working fine about 15 minutes ago. I've removed it completely and reinstalled it and still get the same problem. It was the only window open when it initially crashed.

here's what term spits at me.


> 
joshua@joshua-laptop:~$ nicotine
Nicotine supports "psyco", an inline optimizer for python
code, you can get it at [http://sourceforge.net/projects/psyco/](http://sourceforge.net/projects/psyco/)
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

---

### Post by jarvis13 on 2007-05-26
Top.

I did a complete system reinstall, and things worked great for a few days, but now this problem has returned yet again.

---

### Post by gabe6118 on 2007-06-22
I am having exactly the same problem. I tried uninstalling and re-installing. I've tried removing it completely using the synaptic package manager. Nothing seems to work. I finally had to find another applicaition that does the same thing, although it's not as good as Nicotine+. I was using the 1.2.6 version and I tried updating to 1.6.8 and that didn't work either. HELP! I really like this program.

---

### Post by dunomous on 2007-07-09
Please try this for your fix. It worked for me:

Delete *.db (all files ending with .db) files from your ~/.nicotine/ directory. **Back up your files just in case!!**

This fix was found from [here]("https://bugs.launchpad.net/ubuntu/+source/nicotine/+bug/93251").

---

