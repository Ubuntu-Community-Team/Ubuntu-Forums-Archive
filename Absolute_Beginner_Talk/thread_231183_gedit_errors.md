---
title: "gedit errors"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by Cysman on 2006-08-07
Well hello there, I'm having some issues with gedit.  When I try to use it to modify a text file I get this bunch of gobledy goop:

daddy@daddy-desktop:~$ gedit /etc/modprobe.d/aliases
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ImportError: could not import gtksourceview
Traceback (most recent call last):
  File "/usr/lib/gedit-2/plugins/modelines.py", line 24, in ?
    class ModelinePlugin(gedit.Plugin):
AttributeError: 'module' object has no attribute 'Plugin'

** (gedit:5298): WARNING **: Could not load python module modelines


** (gedit:5298): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5298): WARNING **: Throbber animation not found.

** (gedit:5298): WARNING **: Throbber animation not found.
/bin/sh: /usr/bin/esd: No such file or directory

** (gedit:5298): WARNING **: Throbber animation not found.

** (gedit:5298): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5298): WARNING **: Throbber animation not found.

** (gedit:5298): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed





Is this saying I'm missing something here?

---

### Post by Cysman on 2006-08-07
Anyone?  Without this being remedied, I cant do much with the distro!!

---

### Post by Evil Dax on 2006-08-10
same problem here:

```
dax@metworst:~$ gedit
ImportError: could not import gtksourceview
Traceback (most recent call last):
  File "/usr/lib/gedit-2/plugins/modelines.py", line 24, in ?
    class ModelinePlugin(gedit.Plugin):
AttributeError: 'module' object has no attribute 'Plugin'

** (gedit:8858): WARNING **: Could not load python module modelines


** (gedit:8858): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN  (plugin)' failed

** (gedit:8858): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN  (plugin)' failed

```
Anyone who has an idea?
It's complaining about GTKsourceview, but it's installed already.

PLZ help out....
PS: this is from the moment that I made a clean install with 6.06

---

