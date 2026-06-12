---
title: "&quot;gnome-app-install&quot; - &quot;Add/Remove&quot; issue..."
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by Giamby986 on 2008-02-23
Hi guys,
yesterday I've upgraded my Xubuntu to 7.10...
At a first glance everything worked out great,
but when I've tried to open Add/Remove... it simply won't.

Then I've tried to launch it from terminal with::

*$ sudo gnome-app-install*

with this result::

Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 30, in <module>
    main()
  File "/usr/lib/python2.5/site-packages/AppInstall/activation.py", line 435, in main
    from AppInstall import AppInstall
  File "/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py", line 62, in <module>
    import distros
  File "/usr/lib/python2.5/site-packages/AppInstall/distros/__init__.py", line 2, in <module>
    from Ubuntu import Distribution
  File "/usr/lib/python2.5/site-packages/AppInstall/distros/Ubuntu.py", line 1, in <module>
    import Default
  File "/usr/lib/python2.5/site-packages/AppInstall/distros/Default.py", line 1, in <module>
    from AppInstall.Menu import SHOW_ALL, SHOW_ONLY_SUPPORTED, SHOW_ONLY_FREE, SHOW_ONLY_MAIN, SHOW_ONLY_PROPRIETARY, SHOW_ONLY_THIRD_PARTY, SHOW_ONLY_INSTALLED
  File "/usr/lib/python2.5/site-packages/AppInstall/Menu.py", line 18, in <module>
    import gst
  File "/usr/lib/python2.5/site-packages/gst-0.10/gst/__init__.py", line 144, in <module>
    from _gst import *
RuntimeError: can't initialize module gst: Error re-scanning registry , child terminated by signal


That's it... and that's not ok... eh
I don't know... maybe some gstreamer packages are fighting somewhere;
really don't know where to start, if anyone out here could help ;)
I mean, Synaptic sure is great but I used to like Add/Remove so much...
It would be nice to have it working again.
Thanks guys!!

::Giamby::

---

### Post by bschleusner on 2008-02-23
is python-gst0.10 installed? That is the only thing that comes to mind when looking at the debug output.

---

### Post by Giamby986 on 2008-02-28
Yes python-gst0.10 and python-gst0.10-dbg are correctly installed...
And Add/remove still won't work...

---

### Post by jw5801 on 2008-02-28
You could try running ```
sudo dpkg-reconfigure gnome-app-install
```

---

### Post by Giamby986 on 2008-02-29
Hi guys and thanks jw5801!

I've tried to::

$ sudo dpkg-reconfigure gnome-app-install
Caching application data...
Skipped k3dsurf.desktop: does not include a menu name
Generating mime/codec maps...

Then::

$ sudo gnome-app-install
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 30, in <module>
    main()
  File "/usr/lib/python2.5/site-packages/AppInstall/activation.py", line 435, in main
    from AppInstall import AppInstall
  File "/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py", line 62, in <module>
    import distros
  File "/usr/lib/python2.5/site-packages/AppInstall/distros/__init__.py", line 2, in <module>
    from Ubuntu import Distribution
  File "/usr/lib/python2.5/site-packages/AppInstall/distros/Ubuntu.py", line 1, in <module>
    import Default
  File "/usr/lib/python2.5/site-packages/AppInstall/distros/Default.py", line 1, in <module>
    from AppInstall.Menu import SHOW_ALL, SHOW_ONLY_SUPPORTED, SHOW_ONLY_FREE, SHOW_ONLY_MAIN, SHOW_ONLY_PROPRIETARY, SHOW_ONLY_THIRD_PARTY, SHOW_ONLY_INSTALLED
  File "/usr/lib/python2.5/site-packages/AppInstall/Menu.py", line 18, in <module>
    import gst
  File "/usr/lib/python2.5/site-packages/gst-0.10/gst/__init__.py", line 144, in <module>
    from _gst import *
RuntimeError: can't initialize module gst: Error re-scanning registry , child terminated by signal 

As always..... eehhhh :(


I have also this other error message with pidgin...

"GStreamer Failure", 
"GStreamer failed to initialize.", 
"Error re-scanning registry , child terminated by signal"

and I've heard someone with the same problem with gaim...

I think it's the very same problem I'm having with gnome-app-install, isn't it?
Or at least they are linked...in some dark ways... :)
I really don't know how to fix this... is it a gstreamer problem? and how to solve it?

::Giamby::

---

### Post by jw5801 on 2008-02-29
> **Giamby986 said:**
> Hi guys and thanks jw5801!

I've tried to::

$ sudo dpkg-reconfigure gnome-app-install
Caching application data...
Skipped k3dsurf.desktop: does not include a menu name
Generating mime/codec maps...

Then::

$ sudo gnome-app-install
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 30, in <module>
    main()
  File "/usr/lib/python2.5/site-packages/AppInstall/activation.py", line 435, in main
    from AppInstall import AppInstall
  File "/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py", line 62, in <module>
    import distros
  File "/usr/lib/python2.5/site-packages/AppInstall/distros/__init__.py", line 2, in <module>
    from Ubuntu import Distribution
  File "/usr/lib/python2.5/site-packages/AppInstall/distros/Ubuntu.py", line 1, in <module>
    import Default
  File "/usr/lib/python2.5/site-packages/AppInstall/distros/Default.py", line 1, in <module>
    from AppInstall.Menu import SHOW_ALL, SHOW_ONLY_SUPPORTED, SHOW_ONLY_FREE, SHOW_ONLY_MAIN, SHOW_ONLY_PROPRIETARY, SHOW_ONLY_THIRD_PARTY, SHOW_ONLY_INSTALLED
  File "/usr/lib/python2.5/site-packages/AppInstall/Menu.py", line 18, in <module>
    import gst
  File "/usr/lib/python2.5/site-packages/gst-0.10/gst/__init__.py", line 144, in <module>
    from _gst import *
RuntimeError: can't initialize module gst: Error re-scanning registry , child terminated by signal 

As always..... eehhhh :(


I have also this other error message with pidgin...

"GStreamer Failure", 
"GStreamer failed to initialize.", 
"Error re-scanning registry , child terminated by signal"

and I've heard someone with the same problem with gaim...

I think it's the very same problem I'm having with gnome-app-install, isn't it?
Or at least they are linked...in some dark ways... :)
I really don't know how to fix this... is it a gstreamer problem? and how to solve it?

::Giamby::

I wouldn't think they'd be the same issue. GStreamer has to do with audio and video codecs, so I wouldn't think it would affect gnome-app-install. What version of gnome-app-install have you got installed? If you open synaptic it should be able to tell you. I have 0.4.13-0ubuntu1. So If you have something newer than that then you may want to remove it and then reinstall the Gutsy one using apt-get. I'd probably be inclined to try removing and reinstalling it anyway:

```
sudo -s
apt-get remove gnome-app-install
apt-get clean
apt-get update
apt-get install ubuntu-desktop
```

Removing gnome-app-install should remove ubuntu-desktop (plus a couple of other things) reinstalling ubuntu-desktop should reinstall gnome-app-install as well as whatever else was removed to start off with.

---

