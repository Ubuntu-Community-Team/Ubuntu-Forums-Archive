---
title: "Trying to install Oboe-Sync"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by tm0054 on 2007-03-09
Ok this is driving me a little crazy-

I'm trying to use oboe-sync from MP3Tunes.com and I can't figure out how to make it run.

It requires 'PyQt4' which requires 'SIP' I've attemted to install SIP from both the Add/Remove program area and the command line with absolutely no luck. When I run the PyQt4 config file it relentlessly tells me 'No Module Named sipconfig'. After hours of reading around I still can't get by this...

Anyone have clear directions on how exactly to get Sip, PyQt4 and Oboe-Sync installed? I've alread read most of the other posts in this forum and it hasn't helped.

Sorry for sounding like an idiot but I'm brand new with Ubuntu!

---

### Post by halitech on 2007-03-09
sip

[http://www.riverbankcomputing.com/Downloads/sip4/sip-4.5.2.tar.gz]("http://www.riverbankcomputing.com/Downloads/sip4/sip-4.5.2.tar.gz")

for PyQt4

[http://www.riverbankcomputing.com/Downloads/PyQt4/GPL/PyQt-x11-gpl-4.1.1.tar.gz]("http://www.riverbankcomputing.com/Downloads/PyQt4/GPL/PyQt-x11-gpl-4.1.1.tar.gz")for

download and extract the SIP file first. then from the command line, run

```

python configure.py

```

then download and extract PyQt4
go to that folder in the terminal and run

```

python configure.py

```

then run

```

python run_oboe.py
```

and it should be working

---

### Post by tm0054 on 2007-03-09
I wish that worked!

I get through the first step of running the configure.py file for SIP... It seems to go through but I always get the message 'No Module Named sipconfig' when I run the configure.py file for PyQt4. And of course Oboe Sync won't run without PyQt4.

Could there be some detail I'm missing?

---

### Post by jbelmonte on 2007-03-09
Pardon my noobieness, but I too am having trouble getting Oboe installed and working on my Ununtu 6.10 system. I add the required packages listed in the Oboe Read.me file, but when I run the designated command, 'python run_oboe.py', from the terminal command line I get the following error:

> Traceback (most recent call last):
  File "/home/jbelmonte/Oboe/oboe-2.0/oboe_exe.py", line 1, in ?
    import global_imports
  File "/home/jbelmonte/Oboe/oboe-2.0/global_imports.py", line 7, in ?
    from PyQt4 import Qt, QtCore, QtGui
  File "/usr/lib/python2.4/site-packages/PyQt4/Qt.py", line 4, in ?
    from PyQt4.QtOpenGL import *
ImportError: No module named QtOpenGL

When I search the Synaptic Package Manager for QTOpenGL, the installed python-qt4 package is the only item that is found.

TIA for any suggestions that can point me in the right direction.


[COLOR="Red"]New:

I searched the forum and found my answer.

tm0054 you should try:

Code:
> 
sudo apt-get install python-psyco python-imaging python-qt4 python-qt4-gl python-qt4-sql


Then use 'python2.4 /path/to/oboe/run_oboe.py' where /path/to/oboe/ is replaced with your specific path to run the program. Worked like a charm for me.

These forums are amazing. You can find just about anything you need with a search, but, failing that, there are plenty of people around to help. Thanks everyone.
[/COLOR]

---

### Post by yehoni on 2007-05-01
I keep thinking I've got this one figured out, and suddenly, I'm back to square one.  My latest error message:
```
 File "/home/yehoni/.oboesync/common/ServerConfigReader.py", line 26, in readFlatConfig
    raise Exception('Invalid flat server config file')
Exception: Invalid flat server config file

```
Just over a week in Ubuntu, a host of problems just getting my setup to do all the things I used to do in Windows, and all I can say is, I'd put up with almost any level of initial confusion in exchange for the level of support this forum's existence provides.

---

### Post by bichenoubi on 2007-05-09
Invalid flat server config file solution:
[http://forum.mp3tunes.com/showthread.php?t=121](http://forum.mp3tunes.com/showthread.php?t=121)
:guitar:

---

### Post by al4ie on 2007-05-15
> **bichenoubi said:**
> Invalid flat server config file solution:
[http://forum.mp3tunes.com/showthread.php?t=121](http://forum.mp3tunes.com/showthread.php?t=121)
:guitar:

Thanks very much, that worked a treat :)

---

### Post by DouglasCaixeta on 2007-06-10
I got the python imaging, but I receive the same error.

> 
/home/douglas/.oboesync/common/urllib2.py:93: DeprecationWarning: the gopherlib module is deprecated
  import gopherlib
enabling timeouts
Traceback (most recent call last):
  File "/home/douglas/Desktop/oboe-2.0/oboe_exe.py", line 238, in <module>
    OboePatcher()
  File "/home/douglas/Desktop/oboe-2.0/oboe_exe.py", line 15, in __init__
    self.updateClient()
  File "/home/douglas/Desktop/oboe-2.0/oboe_exe.py", line 97, in updateClient
    self.runClient()
  File "/home/douglas/Desktop/oboe-2.0/oboe_exe.py", line 117, in runClient
    import oboe
  File "/home/douglas/.oboesync/oboe.py", line 9, in <module>
    import imports
  File "/home/douglas/.oboesync/imports.py", line 16, in <module>
    import Image
**ImportError: No module named Image**


The command I used to fix:

> 
 sudo apt-get install python-imaging python-qt4 python-qt4-gl python-qt4-sql


But I still got the same error.

---

### Post by al4ie on 2008-01-28
Hope someone is still reading this/seeing this thread. Having enormous difficulty getting Oboe to run, here's my current output from terminal:

alfie@HAL:~$ python2.4 /home/alfie/.oboesync/run_oboe.py
python2.4: can't open file '/home/alfie/.oboesync/run_oboe.py': [Errno 2] No such file or directory
alfie@HAL:~$ python2.4 /home/alfie/.oboesync/oboe.py
Traceback (most recent call last):
  File "/home/alfie/.oboesync/oboe.py", line 3, in ?
    from app.constants import *
  File "/home/alfie/.oboesync/app/constants.py", line 2, in ?
    from common.locker_util import expanduser
  File "/home/alfie/.oboesync/common/locker_util.py", line 12, in ?
    import urllib, urllib2, random
ImportError: No module named urllib
alfie@HAL:~$ 


Anyone got a clue?

---

### Post by DouglasCaixeta on 2008-01-29
Did you try the new version? 3 ?
 had no problem to install it.

---

