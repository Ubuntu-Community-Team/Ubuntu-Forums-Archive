---
title: "awn extras applets.."
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by patchido on 2008-04-03
i did installed this but for some reason they just appear as a white line why is this??

---

### Post by EnergySamus on 2008-04-03
Read [this]("http://wiki.awn-project.org/FAQ#Why_does_my_bar_have_one_or_more_thin.2C_vertical.2C_white_lines_that_extend_beyond_the_dock.3F")


EnergySamus

---

### Post by patchido on 2008-04-11
i didnt understand what to do.. but this is my output into running it through terminal```
Screen is composited.
APPLET : /usr/local/lib/awn/applets/taskman.desktop
APPLET : /usr/lib/awn/applets/trasher.desktop
APPLET : /usr/lib/awn/applets/weather.desktop
APPLET : /usr/lib/awn/applets/media-control.desktop

** (awn-applet-activation:7171): WARNING **: This desktop file does not exist /usr/lib/awn/applets/trasher.desktop


** (awn-applet-activation:7175): WARNING **: Unable to load module /usr/lib/awn/applets/media-control/mediacontrol.py


** (awn-applet-activation:7175): WARNING **: /usr/lib/awn/applets/media-control/mediacontrol.py: invalid ELF header

** (awn-applet-activation:7175): WARNING **: Could not create plug


** (awn-applet-activation:7173): WARNING **: Unable to load module /usr/lib/awn/applets/weather/weather.py


** (awn-applet-activation:7173): WARNING **: /usr/lib/awn/applets/weather/weather.py: invalid ELF header

** (awn-applet-activation:7173): WARNING **: Could not create plug

APPLET : /usr/lib/awn/applets/showdesktop.desktop

** (awn-applet-activation:7179): WARNING **: This desktop file does not exist /usr/lib/awn/applets/shinyswitcher.desktop

APPLET : /usr/lib/awn/applets/shinyswitcher.desktop
APPLET : /usr/lib/awn/applets/stacks.desktop

** (awn-applet-activation:7177): WARNING **: Unable to load module /usr/lib/awn/applets/showdesktop/showdesktop.py


** (awn-applet-activation:7177): WARNING **: /usr/lib/awn/applets/showdesktop/showdesktop.py: invalid ELF header

** (awn-applet-activation:7177): WARNING **: Could not create plug


** (awn-applet-activation:7181): WARNING **: Unable to load module /usr/lib/awn/applets/stacks/stacks_applet.py


** (awn-applet-activation:7181): WARNING **: /usr/lib/awn/applets/stacks/stacks_applet.py: invalid ELF header

** (awn-applet-activation:7181): WARNING **: Could not create plug



```

---

### Post by EnergySamus on 2008-04-11
... I'm not sure then... Sorry!:cry:

EnergySamus

---

### Post by moonbeam on 2008-04-11
> **patchido said:**
> i didnt understand what to do.. but this is my output into running it through terminal```
Screen is composited.
APPLET : /usr/local/lib/awn/applets/taskman.desktop
APPLET : /usr/lib/awn/applets/trasher.desktop
APPLET : /usr/lib/awn/applets/weather.desktop
APPLET : /usr/lib/awn/applets/media-control.desktop

<SNIP>

** (awn-applet-activation:7181): WARNING **: /usr/lib/awn/applets/stacks/stacks_applet.py: invalid ELF header

** (awn-applet-activation:7181): WARNING **: Could not create plug



```

Looks like you're using an awn-core with a version < 0.2.4 with an awn-extras >=0.2.4.

In general you probably want to remove all signs of awn from your system.

Then try

[http://ubuntuforums.org/showthread.php?t=385981&highlight=avant+window+navigator](http://ubuntuforums.org/showthread.php?t=385981&highlight=avant+window+navigator)

or 

[https://launchpad.net/~awn-testing/+archive](https://launchpad.net/~awn-testing/+archive)

(note that today the awn-testing PPA is broken from unknown reasons... it is being researched).

General install information is at [http://wiki.awn-project.org/Installation](http://wiki.awn-project.org/Installation)

---

### Post by patchido on 2008-04-15
i have awn curves

---

### Post by patchido on 2008-04-15
i tried that and i still can make that work

---

