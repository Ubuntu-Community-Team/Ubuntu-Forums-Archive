---
title: "I think I've got 2 versions of the same program installed, how do I remove one?"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by Thenotsowyzewun on 2007-01-01
I'm trying to use a program called Oboe Sync 2.0 which is coded in Python and uses the PyQt GUI.
Anyway it won't run; it gives this error msg:

>   File "*/path/to*/oboe-2.0/global_imports.py", line 4, in <module>
    import urllib, urllib2, PyQt4, sip, sets, ConfigParser, commands
ImportError: No module named PyQt4

So I took a look at that file, global_imports.py and line 4 says 
import urllib, urllib2, PyQt4, sip, sets, ConfigParser, commands.

Again in context:

> # Place _all_ dependencies here so py2exe includes them.

**import urllib, urllib2, PyQt4, sip, sets, ConfigParser, commands**
import optparse

from PyQt4 import Qt, QtCore, QtGui

So I checked the dependencies:

> REQUIREMENTS
 
In order to use Oboe in linux you will need Python 2.3 or above, available from [http://www.python.org/](http://www.python.org/), and PyQt4, which is available from Riverbank Software at [http://www.riverbankcomputing.co.uk/pyqt/](http://www.riverbankcomputing.co.uk/pyqt/). Also required is the PIL library available from [http://www.pythonware.com/products/pil/](http://www.pythonware.com/products/pil/). Not necessary, but recommended, is the Psyco library available at [http://psyco.sourceforge.net/](http://psyco.sourceforge.net/).
 and ran this command to install them properly:

> sudo apt-get install python-psyco python-imaging python-qt4 python-qt4-gl python-qt4-sql

Unfortunately, I'd already tried to install Python without using apt-get (by downloading the various bits from the sites suggested above in REQUIREMENTS). I managed to install python, but PyQt had dependencies of it's own, so it all got in a bit of a mess.

Anyway, when I ran into the error message above (the first one, at the top of the post), I searched google and found this:

[URL="http://mats.gmd.de/pipermail/pykde/2004-July/008172.html"]
http://mats.gmd.de/pipermail/pykde/2004-July/008172.html[/URL]

It appears the problem is that I have more than one copy of Python installed, the program is perhaps running with one and that's not the one that has PyQt setup correctly by apt-get (that's pretty much what the above link suggests).

So I ran > whereis python (there's probably a better way to check, but I don't know it) and it looks like I have 2, maybe 3 versions installed!:

> python: /usr/bin/python /usr/bin/python2.4 /etc/python /etc/python2.4 /usr/lib/python2.3 /usr/lib/python2.4 /usr/lib/python2.5 /usr/X11R6/bin/python /usr/X11R6/bin/python2.4 /usr/bin/X11/python /usr/bin/X11/python2.4 /usr/local/bin/python2.5 /usr/local/bin/python2.5-config /usr/local/bin/python /usr/local/lib/python2.4 /usr/local/lib/python2.5 /usr/include/python2.4 /usr/include/python2.5 /usr/share/python /usr/share/man/man1/python.1.gz

I don't usually uninstall anything, since space doesn't require it, and I don't want to mess up any dependencies.
So rather than use apt-get, I went into Synaptic Package Manager and tried to remove Python. Completely. Problem is it tells me I've got a bunch of dependencies (doesn't come as much of a surprise!).

What should I do?

Thanks very much for reading this far!

---

### Post by Thenotsowyzewun on 2007-01-01
Someone gave me a suggestion elsewhere, and I wanted to keep the thread upto date so:

[http://ubuntuforums.org/showpost.php?p=1956719&postcount=8]("http://ubuntuforums.org/showpost.php?p=1956719&postcount=8")
Read that first or this'll make no sense.

The suggestion didn't work, but it might've helped; maybe I'm wrong about having to remove one copy of Python at all, maybe if I just execute the command differently it'll know where to find PyQt.

Any suggestions? Cheers for reading!

---

