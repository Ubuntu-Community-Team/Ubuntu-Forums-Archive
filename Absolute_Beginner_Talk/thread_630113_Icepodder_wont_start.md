---
title: "Icepodder wont start"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by Namingishard on 2007-12-03
Im running 7.10 and when I try to run Icepodder it opens for a split second and then closes.
Here is the error I get when I run it through the command line

```
CastPodderGui.py:48: DeprecationWarning: The wxPython compatibility package is no longer automatically generated or actively maintained.  Please switch to the wx package as soon as possible.
  from   wxPython.wx import *
[<class 'ipodder.players.XMMSPlayer'>, <class 'ipodder.players.NoPlayer'>]
Beep-Media-Player couldn't be imported
Traceback (most recent call last):
  File "CastPodderGui.py", line 3623, in <module>
    main()
  File "CastPodderGui.py", line 3617, in main
    myApp = iPodderGui(ipodder)
  File "CastPodderGui.py", line 685, in __init__
    wx.App.__init__(self, False, None)
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 7757, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 7354, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "CastPodderGui.py", line 1519, in OnInit
    self.InitHooks()
  File "CastPodderGui.py", line 1876, in InitHooks
    for att, method in inspect.getmembers(self, inspect.ismethod): 
  File "/usr/lib/python2.5/inspect.py", line 206, in getmembers
    value = getattr(object, key)
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 9331, in GetAcceleratorTable
    return _core_.Window_GetAcceleratorTable(*args, **kwargs)
TypeError: in method 'Window_GetAcceleratorTable', expected argument 1 of type 'wxWindow *'

```

---

### Post by Namingishard on 2007-12-04
Anyone got any suggestions on how to fix this? Or a suggestion for a program like this one.

---

### Post by six^letters^digits on 2007-12-11
with synaptic package manager install :
python
python-xmms
bittorrent
python-wxgtk2.6
python-pyrss2gen
python-feedparser
libwxgtk
python-chardet (For German users)

download
[http://www.icepodder.com/wp-content/uploads/2007/02/IcePodder-5.4.tar.bz2]("http://www.icepodder.com/wp-content/uploads/2007/02/IcePodder-5.4.tar.bz2")
extract to a <directory>

in a terminal:
$ cd <that directory>
<that directory>$ sudo bash install.sh
$ cd /usr/share/icepodder
$ python CastPodderGui.py

...... then it should be running
you can watch the log in the terminal window
possibly find bugs

see
[Howto: Install icepodder (Gutsy Gibbon)]("http://ubuntuforums.org/showthread.php?t=607186")
[http://ubuntuforums.org/showthread.php?t=607186](http://ubuntuforums.org/showthread.php?t=607186)



for another solution


:guitar:   =;

---

### Post by solitone on 2007-12-30
> **Namingishard said:**
> Im running 7.10 and when I try to run Icepodder it opens for a split second and then closes.
Here is the error I get when I run it through the command line

```

  [...]
  line 9331, in GetAcceleratorTable
    return _core_.Window_GetAcceleratorTable(*args, **kwargs)
  TypeError: in method 'Window_GetAcceleratorTable', expected argument 1 of type 'wxWindow *'

```

Hi, I had the very same issue. Make sure you do not have the package _python-wxgtk2.8_ installed. You just need python-wxgtk2.6.

Cheers!

---

