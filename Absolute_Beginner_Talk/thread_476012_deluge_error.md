---
title: "deluge error"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2007-06-16
zerobinary@zerobinary:~$ deluge
no existing Deluge session
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
Applying preferences
Raising error: 
Error: ''
Traceback (most recent call last):
  File "/usr/bin/deluge", line 63, in <module>
    interface = deluge.interface.DelugeGTK()
  File "/usr/lib/python2.5/site-packages/deluge/interface.py", line 95, in __init__
    '%s %s'%(common.PROGRAM_NAME, common.PROGRAM_VERSION), common.CONFIG_DIR)
  File "/usr/lib/python2.5/site-packages/deluge/core.py", line 237, in __init__
    self.sync()
  File "/usr/lib/python2.5/site-packages/deluge/core.py", line 655, in sync
    raise e
deluge.core.InvalidEncodingError: ''

---

### Post by dbbolton on 2007-06-16
> **zerobinary said:**
> zerobinary@zerobinary:~$ deluge
no existing Deluge session
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
Applying preferences
Raising error: 
Error: ''
Traceback (most recent call last):
  File "/usr/bin/deluge", line 63, in <module>
    interface = deluge.interface.DelugeGTK()
  File "/usr/lib/python2.5/site-packages/deluge/interface.py", line 95, in __init__
    '%s %s'%(common.PROGRAM_NAME, common.PROGRAM_VERSION), common.CONFIG_DIR)
  File "/usr/lib/python2.5/site-packages/deluge/core.py", line 237, in __init__
    self.sync()
  File "/usr/lib/python2.5/site-packages/deluge/core.py", line 655, in sync
    raise e
deluge.core.InvalidEncodingError: ''
by what means did you install deluge?

---

### Post by zvacet on 2007-06-16
[http://www.getdeb.net/search.php?keywords=deluge]("http://www.getdeb.net/search.php?keywords=deluge")

---

### Post by zerobinary on 2007-06-16
i reinstall it still no working 
i think i deleted the python dependance but i don't know which 
plz tell me what dependance i need

---

### Post by zvacet on 2007-06-17
If you still have source file wich you tryed to compile look **read me** file or **install** file.There you heve list of all dependencies you need.Look in synaptic and chek are they all there.If something is missing install it with synaptic.

---

### Post by zerobinary on 2007-06-17
is fix and i lost all my old data  thx

---

