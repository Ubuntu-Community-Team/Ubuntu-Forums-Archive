---
title: "[SOLVED] visual effects preferences not working. prefs button not working."
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by iain010100 on 2007-11-01
Hi,

I've been messing around with the advanced appearance preferences and now when I click on the preferences tab nothing happens.

System > preferences > appearance > visual effects tab > preferences (next to custom button)

And, when I check "custom," all the effects like cube, fade, wabble, etc. don't work. Something's broken. Is there a way to restore or reinstall all of the appearance settings without doing a clean install of Ubuntu?

---

### Post by thesm on 2007-11-01
[http://ubuntuforums.org/showthread.php?t=591020&highlight=ccsm](http://ubuntuforums.org/showthread.php?t=591020&highlight=ccsm)

good luck.

---

### Post by iain010100 on 2007-11-01
alt+f2 > ccsm does nothing. No window, no alert. Nothing. 

The output from [FONT="Courier New"]dpkg -l | grep compiz[/FONT] gives me this:

ii  compiz                                     1:0.6.0+git20071008-0ubuntu1         OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1         OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1           Collection of extra plugins from OpenCompositing for Com
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2           Collection of plugins from OpenCompositing for Compiz
ii  compiz-fusion-plugins-unofficial           0.0.2~git20070921+3v1ubuntu0         Collection of UNOFFICIAL fusion plugins for Compiz
ii  compiz-fusion-plugins-unsupported          0.5.2~git20071006+3v1ubuntu0         Collection of plugins for Compiz - Unsupported
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1         OpenGL window and compositing manager - GNOME window dec
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1         OpenGL window and compositing manager - plugins
ii  compizconfig-settings-manager              0.6.99~git20071005+3v1ubuntu0        Plugin and configuration tool - Compiz Fusion Project
ii  libcompizconfig-backend-gconf              0.6.0~git20071003+3v1ubuntu0         GNOME Backend for the Compiz Configuration System
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3           Settings library for plugins - OpenCompositing Project
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1           Compiz configuration system bindings

Should I try to remove the compiz=fusion plugins?

---

### Post by thesm on 2007-11-01
Running ccsm with alt-f2 won't give you the output, if you open a terminal first and run it what do you get?

You can try removing the unsupported plugins, if that fails maybe try reinstalling ccsm like in the link.

---

### Post by iain010100 on 2007-11-01
My mistake about ccsm output. Here's what I get.

Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

---

### Post by iain010100 on 2007-11-01
The link you mentioned was useful in letting me remove the "preferences" button in appearances / visual effects tab.

I followed the instructions for installing CompizConfig ([http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion))

I can now activate the Advanced Desktop Effects Settings window (via ccsm or the preferences menu). The problem I have now is that the settings don't take effect. When I go to system > preferences > appearance > visual effects, I'm not able to change the setting beyond NONE. If I try to do so, all of the buttons get greyed out for several seconds, then the NONE choice gets reset automatically.

---

### Post by iain010100 on 2007-11-01
ok, so after I uninstalled one of the compiz fusion packages everything worked, minus some plug-ins.

---

