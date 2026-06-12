---
title: "Open RPG Installer"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by beastrace91 on 2007-09-17
Hey there everyone,
I've spent 2 hours so far trying to get the program Open RPG to work on my Kubuntu 7.04 and I am having no luck. I've gone threw most of the guides out there detailing how to install python and wxpython but it just wont work. I keep getting this message when I use the 'python start.py' command to try to start open rpg:

*WARNING* failed to import wxPython.
Download the correct version here: [http://openrpg.digitalxero.net/](http://openrpg.digitalxero.net/)
If you are running the server with no gui you can ignore this message

I have installed wxPython more than once but it still doesn't seem to be working... Any ever get this program working before? Or anyone know of a place I can get a .deb installer for it?

~J3ff

---

### Post by HunterRose on 2007-11-12
I am having something similar, except i got to the point where I can start this is what i got:
>	python2.5: can't open file 'start.py': [Errno 2] No such file or directory
hunterrose@HunterRose:~$ openrpg-client
/usr/share/openrpg/orpg/plugins.py:1: DeprecationWarning: The wxPython compatibility package is no longer automatically generated or actively maintained. Please switch to the wx package as soon as possible.
from wxPython.wx import *
Rooting OpenRPG at: /usr/share/openrpg
[WARNING] Could not create approot file.
[WARNING] Automatic directory resolution not configured.
Traceback (most recent call last):
File "./start.py", line 6, in <module>
import orpg.main
File "/usr/share/openrpg/orpg/main.py", line 35, in <module>
from orpg.orpg_windows import *
File "/usr/share/openrpg/orpg/orpg_windows.py", line 43, in <module>
from wxPython.html import *
File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wxPython/html.py", line 151, in <module>
wxHtmlWindowEvent = wx.html.HtmlWindowEvent
AttributeError: 'module' object has no attribute 'HtmlWindowEvent'

---

### Post by basotl on 2007-12-19
I just had to use the more up to date package from the [unofficial download site]("http://openrpg.digitalxero.net/wiki/").

I guess the issue was addressed but the package at Sourceforge hasn't been updated.

---

