---
title: "Nicotine+ Freezes"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by gidra on 2007-02-17
It used to work fine, but all of a sudden when i start nicotine it pops up a blank window and just freezes there, any ideas ?

BTW terminal gives this :

Nicotine supports "psyco", an inline optimizer for python
code, you can get it at [http://sourceforge.net/projects/psyco/](http://sourceforge.net/projects/psyco/)
Bogus config option npplayer section players
Bogus config option npformat section players
Bogus config option npothercommand section players
Bogus config option npformatlist section players
Bogus config option trayicon section ui
Bogus config option soundenabled section ui
Bogus config option soundcommand section ui
Bogus config option speechenabled section ui
Bogus config option soundtheme section ui
Bogus config option enabletransferbuttons section transfers
Bogus config option npplayer section players
Bogus config option npformat section players
Bogus config option npothercommand section players
Bogus config option npformatlist section players
Bogus config option trayicon section ui
Bogus config option soundenabled section ui
Bogus config option soundcommand section ui
Bogus config option speechenabled section ui
Bogus config option soundtheme section ui
Bogus config option enabletransferbuttons section transfers
Traceback (most recent call last):
  File "/usr/bin/nicotine", line 149, in ?
    app = frame.MainApp(config)
  File "/var/lib/python-support/python2.4/pynicotine/gtkgui/frame.py", line 1383, in __init__
    self.frame = testwin(config)
  File "/var/lib/python-support/python2.4/pynicotine/gtkgui/frame.py", line 338, in __init__
    if self.np.config.needConfig():
  File "/var/lib/python-support/python2.4/pynicotine/config.py", line 86, in needConfig
    if self.sections[i][j] is None or self.sections[i][j] == '' and i not in ("userinfo", "ui", "ticker", "players") and j not in ("incompletedir", "autoreply", 'afterfinish','afterfolder', 'geoblockcc'):
  File "/usr/lib/python2.4/UserDict.py", line 168, in __cmp__
    return cmp(dict(self.iteritems()), other)
  File "/usr/lib/python2.4/UserDict.py", line 100, in iteritems
    for k in self:
  File "/usr/lib/python2.4/UserDict.py", line 87, in __iter__
    for k in self.keys():
  File "/usr/lib/python2.4/shelve.py", line 98, in keys
    return self.dict.keys()
  File "/usr/lib/python2.4/site-packages/PIL/__init__.py", line 244, in keys
    
bsddb.db.DBPageNotFoundError: (-30987, 'DB_PAGE_NOTFOUND: Requested page not found')

---

### Post by tijmz on 2007-04-07
I have exactly the same thing. I tried reinstalling both nicotine+ and python, but no change at all. Dropping back to 1.0.8 from the repositories instead of nicotine+-1.2.4.1 didn't make any difference, either.

---

### Post by dunomous on 2007-07-09
Please try this for your fix. It worked for me:

Delete *.db (all files ending with .db) files from your ~/.nicotine/ directory. Back up your files just in case!!

This fix was found from [here]("https://bugs.launchpad.net/ubuntu/+source/nicotine/+bug/93251").

---

### Post by xOrangeFirex on 2008-04-07
I have the same issue, but I have no .db files to delete from where I download my music and things to. Any idea what I should do? I had this issue and ended up reinstalling my entire OS so that I could have nicotine, so getting this working would really be good b/c I dont want to have to reinstall Ubuntu again.

---

