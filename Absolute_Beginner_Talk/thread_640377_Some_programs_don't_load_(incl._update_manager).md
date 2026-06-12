---
title: "Some programs don't load (incl. update manager)"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by JohnMoriarty on 2007-12-14
A selection of programs won't load for me. The most obvious one is update-manager. The updates available icon appears on the notification panel, but clicking on it does nothing; selecting show updates also does nothing, but selecting install updates works fine. Update-manager won't run from the system menu, and from terminal I get the following:
```

johnmoriarty@johnmoriarty:~$ sudo update-manager
[sudo] password for johnmoriarty:
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 32, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 59, in <module>
    import dbus
  File "/var/lib/python-support/python2.5/dbus/__init__.py", line 96, in <module>
    from dbus._dbus import Bus, SystemBus, SessionBus, StarterBus
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 45, in <module>
    from dbus.bus import BusConnection
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 22, in <module>
    import logging
  File "logging/__init__.py", line 38, in <module>
  File "/usr/lib/python2.5/threading.py", line 13, in <module>
    from collections import deque
ValueError: method cannot be both class and static

```

The same problem appears when I try to load Add/Remove Programs and Serpentine. It appears to be loading, and "Starting Serpentine..." appears on the task bar, but then disappears and nothing happens. From terminal I get the following:
```

johnmoriarty@johnmoriarty:~$ serpentine
Traceback (most recent call last):
  File "/usr/bin/serpentine", line 114, in <module>
    from serpentine.common import SerpentineError
  File "/usr/lib/python2.5/site-packages/serpentine/__init__.py", line 40, in <module>
    from serpentine.mastering import GtkMusicList, MusicListGateway
  File "/usr/lib/python2.5/site-packages/serpentine/mastering.py", line 24, in <module>
    import logging
  File "logging/__init__.py", line 38, in <module>
  File "/usr/lib/python2.5/threading.py", line 13, in <module>
    from collections import deque
ValueError: method cannot be both class and static
```

Any ideas? I'm new to Linux so I'll need pretty full explanations please.

Thanks
John

---

### Post by Anicka on 2007-12-14
It's difficult to say what is wrong, but you can try to reinstall the programs that are messing with you. I would suggest that you clean the cache of downloaded packages and reinstall with freshly downloaded ones. Like this:```
sudo aptitude clean
sudo aptitude reinstall python2.5 update-manager serpentine
```You can add any programs on the last line that you have trouble with. Also if you would give some more information, which version are you using, is it a fresh install or update from an older version, how long have you had this install, was it ever working properly, any other programs that don't seem to work...?

---

### Post by JohnMoriarty on 2007-12-14
Thanks for your reply. Sorry I wasn't clearer (clean install, 7.10, run ok for about a month).

Tried your suggestion, which seemed to produce vast quantities of errors, and was going to post it here when I discovered my file system appeared to have become read only (and nothing would usefully work). Rebooted, and it failed to boot. Went into recovery console, manually ran fsck, which fixed allsorts, and everything now appears to work.

So I don't know what all that was about,
but thanks
John

---

