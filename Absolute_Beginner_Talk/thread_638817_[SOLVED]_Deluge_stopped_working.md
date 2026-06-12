---
title: "[SOLVED] Deluge stopped working?"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by tony.morse on 2007-12-12
Hi, 
I've been using Deluge for ages and suddenly its stopped working?  I've tried re-installing but no luck. this is what I get...

:~$ deluge
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
Capping download to -1 bytes per second
Capping upload to -1 bytes per second
Traceback (most recent call last):
  File "/usr/bin/deluge", line 140, in <module>
    start_deluge()
  File "/usr/bin/deluge", line 127, in start_deluge
    interface = deluge.interface.DelugeGTK()
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 53, in __init__
    '%s %s'%(common.PROGRAM_NAME, common.PROGRAM_VERSION), common.CONFIG_DIR)
  File "/var/lib/python-support/python2.5/deluge/core.py", line 258, in __init__
    self.state = pickle.load(pkl_file)
  File "/usr/lib/python2.5/pickle.py", line 1370, in load
    return Unpickler(file).load()
  File "/usr/lib/python2.5/pickle.py", line 858, in load
    dispatch[key](self)
  File "/usr/lib/python2.5/pickle.py", line 880, in load_eof
    raise EOFError
EOFError


any idea how I can fix this??

---

### Post by FakeOutdoorsman on 2007-12-12
```
rm ~/.config/deluge/persistent.state
```

You may have to re-add your torrents after you run the above command.

---

### Post by tony.morse on 2007-12-13
Cool, that fixed it thanks!!!

---

### Post by ctyc on 2007-12-13
a complete uninstall then new install of latest deluge also worked.

---

