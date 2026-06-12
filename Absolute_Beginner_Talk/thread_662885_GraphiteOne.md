---
title: "GraphiteOne"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by almoravid on 2008-01-09
I've follow the step from [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=528221](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=528221) to install graphiteone CAD but the when i use command line to run the program i got this output and the program doesnt appear

```
almoravid@ubuntu-almoravid:~$ /opt/GraphiteOne/bin/graphiteone --ogl=yes
/opt/GraphiteOne/lib/qt.py:46: RuntimeWarning: Python C API version mismatch for module libsip: This Python has API version 1013, module libsip has version 1012.
  import libsip
/opt/GraphiteOne/lib/qt.py:50: RuntimeWarning: Python C API version mismatch for module libqtc: This Python has API version 1013, module libqtc has version 1012.
  import libqtc
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/opt/GraphiteOne/lib/HPY.py:2: RuntimeWarning: Python C API version mismatch for module HPYc: This Python has API version 1013, module HPYc has version 1012.
  import HPYc
/opt/GraphiteOne/lib/qt.py:46: RuntimeWarning: Python C API version mismatch for module libsip: This Python has API version 1013, module libsip has version 1012.
  import libsip
/opt/GraphiteOne/lib/qt.py:50: RuntimeWarning: Python C API version mismatch for module libqtc: This Python has API version 1013, module libqtc has version 1012.
  import libqtc
/opt/GraphiteOne/lib/qtxml.py:38: RuntimeWarning: Python C API version mismatch for module libqtxmlc: This Python has API version 1013, module libqtxmlc has version 1012.
  import libqtxmlc
/opt/GraphiteOne/lib/oc.py:6: RuntimeWarning: Python C API version mismatch for module libocc: This Python has API version 1013, module libocc has version 1012.
  import libocc
GOneStatusBar : running without parametric design extension
GOnePersistentElement : running without parametric design extension
Traceback (most recent call last):
  File "/opt/GraphiteOne/lib/graphiteone.py", line 15, in <module>
    from graphiteoneapplication import GOneApplication
  File "/opt/GraphiteOne/lib/graphiteoneapplication.py", line 25, in <module>
    from graphiteoneframe import *
  File "/opt/GraphiteOne/lib/graphiteoneframe.py", line 21, in <module>
    from graphiteonemenudata import *
  File "/opt/GraphiteOne/lib/graphiteonemenudata.py", line 15, in <module>
    from graphiteonemenuwidget import *
  File "/opt/GraphiteOne/lib/graphiteonemenuwidget.py", line 16, in <module>
    from graphiteoneparteditor import *
  File "/opt/GraphiteOne/lib/graphiteoneparteditor.py", line 15, in <module>
    from graphiteonepartelement import GOnePartElement
  File "/opt/GraphiteOne/lib/graphiteonepartelement.py", line 22, in <module>
    from graphiteonepartshadowelement import GOnePartShadowElement
  File "/opt/GraphiteOne/lib/graphiteonepartshadowelement.py", line 18, in <module>
    from graphiteonetciohandler import GOneTCIOElementHandler
  File "/opt/GraphiteOne/lib/graphiteonetciohandler.py", line 25, in <module>
    from graphiteoneworkingplane import GOneWorkingPlane
  File "/opt/GraphiteOne/lib/graphiteoneworkingplane.py", line 19, in <module>
    from graphiteoneutils import TC_TrsfToHoopsMatrix
  File "/opt/GraphiteOne/lib/graphiteoneutils.py", line 802
SyntaxError: Non-ASCII character '\xf8' in file /opt/GraphiteOne/lib/graphiteoneutils.py on line 802, but no encoding declared; see http://www.python.org/peps/pep-0263.html for details

```

---

### Post by LowSky on 2008-01-09
this is the error

SyntaxError: Non-ASCII character '\xf8' in file /opt/GraphiteOne/lib/graphiteoneutils.py on line 802, but no encoding declared

it also  says to go here

[http://www.python.org/peps/pep-0263.html](http://www.python.org/peps/pep-0263.html)


i'm a noob on on encoding but the link says that certain languages are not compatible.

---

### Post by mosaic2s on 2008-02-05
have installed graphiteone - converted rpm to deb using alien. then installed.
however, can not find the program in the menu list. Nor locate it elsewhere.

How to search for the installed program folder?

---

### Post by deepthought on 2008-02-10
to Almoravid

have you installed "libqt3-mt" ?
Then try to start graphiteone in a terminal with "bash graphiteone --python=/usr/bin/python2.4" 
-> this will solve the Problem (RuntimeWarning: Python C API version mismatch for module libsip: This Python has API version 1013, module libsip has version 1012.)

to mosaic2s
graphiteone is installed in "/opt/GraphiteOne"
the starter is "/opt/GraphiteOne/bin/graphiteone"
Start graphiteone in a terminal with "bash graphiteone --python=/usr/bin/python2.4"

---

