---
title: "Gaphor doesn't start."
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by Golyadkin on 2007-08-17
I am trying to install [Gaphor]("http://gaphor.devjavu.com/"), but have a lot of trouble with it. I tried installing gaphor_0.8.1-5.1ubuntu1_all.deb, but it doesn't start. I also tried to convert the gaphor-0.9.2.tar.gz sourcepackage to a .deb with alien, but the installation didn't work. Then I also tried to install it with easy_install -D gaphor, which works with Python Eggs, also to no avail...

This is the error I get when starting Gaphor:
```

Traceback (most recent call last):
  File "/usr/bin/gaphor", line 13, in <module>
    gaphor.main(model)
  File "/usr/lib/python2.5/site-packages/gaphor-0.11.2-py2.4.egg/gaphor/__init__.py", line 36, in main
    from gaphor.application import Application
  File "/usr/lib/python2.5/site-packages/gaphor-0.11.2-py2.4.egg/gaphor/application.py", line 13, in <module>
    from zope import component
  File "/usr/lib/python2.5/site-packages/zope.component-3.4dev_r72749-py2.5.egg/zope/component/__init__.py", line 19, in <module>
    import zope.deferredimport
  File "/usr/lib/python2.5/site-packages/zope.deferredimport-3.4.0-py2.5.egg/zope/deferredimport/__init__.py", line 1, in <module>
    from zope.deferredimport.deferredmodule import initialize
  File "/usr/lib/python2.5/site-packages/zope.deferredimport-3.4.0-py2.5.egg/zope/deferredimport/deferredmodule.py", line 20, in <module>
    import zope.proxy
ImportError: No module named proxy

```

---

### Post by Golyadkin on 2007-08-17
Now I also tried the 0.11 version, same effect, doesn't work at all.

---

### Post by Terl on 2007-08-17
Have you installed all it requires?  I noticed here ([Install Requirements]("http://gaphor.sourceforge.net/manual/chap-install.html#sect-install-linux")) that Diacanvas2 is required and it further mentions python bindings.

I see in your sig, Ubuntu 64 bit.  Does this program work on 64 bit?  I did not check the site thoroughly.  I did notice thay have a ticket system, have you tried through there to get assistance.  Go here to:  [Submit ticket]("http://gaphor.devjavu.com/projects/gaphor/newticket")

---

### Post by Golyadkin on 2007-08-18
Thanks for the reply Terl, 

I have python-diacanvas2 installed, but for python-gnome, py-gnome and gnome-python there are no installation candidates.

```

E: Couldn't find package py-gnome
E: Couldn't find package gnome-python
Package python-gnome is not available, but is referred to by another package.
E: Package python-gnome has no installation candidate

```

I am running 32 bit Ubuntu now by the way, this is on another computer. So the cpu architecture is not the problem. I think I am going to try and compile diacanvas2 by hand.

---

### Post by Golyadkin on 2007-08-18
I am trying to compile diacanvas2 manually here, but I get a strange error when I do:

```

checking for DIACANVAS2... configure: error: Package requirements (glib-2.0 >= 2.0.0
             gobject-2.0 >= 2.0.0
             libart-2.0 >= 2.0.0
             libgnomecanvas-2.0 >= 2.0.0
             ) were not met:

No package 'libart-2.0' found
No package 'libgnomecanvas-2.0' found

```

Now, I run this command:
```

golyadkin@venti:~/temp/diacanvas2-0.15.4$ sudo apt-get install libart-2.0-2 libgnomecanvas2-0 
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libart-2.0-2 is already the newest version.
libgnomecanvas2-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
But it says both are already installed. However, the names are very slightly different... How can I solve this?

---

### Post by Phrawm48 on 2007-09-17
I'll add to the thread that there have been a lot of bugs filed on this, per:

[URL="http://www.google.com/search?q=Linux+Gaphor+%22couldn%27t+make+the+type+%60CanvasGroup%27+ready%22+&hl=en&filter=0"]Linux Gaphor "couldn't make the type `CanvasGroup' ready"
[/URL]
Per some of the bug reports, it appears that one can download and install a newer version of Gaphor outside of Synaptic that will run.  Insofar as this problem has been around since Edgy, one can but wonder why the Feisty (and presumably later) repositories still have the older, non-running version...

**EDIT**:  After my original post, I downloaded and un-zipped Gaphor 0.9.2 (no installation necessary or even possible).  I can run it from a local directory; it starts from a shell script.  Although not perfect -- I can run the script from its directory and nowhere else -- I can at least get Gaphor to run...

Cheers & hope this helps,
Ric

SFO

---

