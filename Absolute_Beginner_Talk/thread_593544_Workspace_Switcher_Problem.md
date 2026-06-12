---
title: "Workspace Switcher Problem"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by gkjohn on 2007-10-27
Hi,

I'm running Gutsy with Desktop Effects enabled and using the Restricted Nvidia driver. However, I have one problem when running the above. I can't switch desktops/workspace using either the keyboard shortcut (ctrl+alt+left/right arrow) or by clicking on the desktop icon in the bottom right of the screen. I have two desktops.

However, if I disable Desktop Effects, this work just fine, both via keyboard and via mouse.

Any idea how I can get it to work with Desktop Effects enabled?

---

### Post by jachymc on 2007-10-27
You have to set your compiz, so it uses only 1 desktop: start Compiz Settings manager, go to "general", select "Desktop size" tab. For cube, use Horizontal virtual size "4", Vertical virtual size "1" and Number of desktops "1". The last number is the one, you need to change.

If you do not have compiz settings manager available (accessable via "Advanced Desktop Setings"), make sure, compizconfig-settings-manager is installed.

---

### Post by gkjohn on 2007-10-27
Thanks for the tip. 

I installed it but I can't seem to access it via the Menu or the Terminal. At best, I find a new option under System>Preferences>Appearance>Visual Effects>Custom. I selected  'Preferences" under the Custom option and changed the settings you asked me to and restarted. However, on restart, Custom does not stay checked. It reverts to Extra. 

I ran:

```
dpkg -l | grep compiz
```

and this is the output:

```
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1          OpenGL window and compositing manager
rc  compiz-extra                               0.3.6.1-0ubuntu2                      extra third party plugins for compiz
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1            Collection of extra plugins from OpenComposi
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1          OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 1:0.3.6-1ubuntu13                     OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1          OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1            Compiz configuration settings manager
rc  gnome-compiz-manager                       0.10.3-0ubuntu1                       Compiz Gnome Manager
ii  libcompizconfig-backend-gconf              0.6.0~git20071003+3v1ubuntu0          GNOME Backend for the Compiz Configuration S
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3            Settings library for plugins - OpenCompositi
rc  libgnome-compiz-manager0                   0.10.3-0ubuntu1                       Compiz Gnome Manager
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1            Compiz configuration system bindings
```

Any ideas as to what might be wrong?

---

