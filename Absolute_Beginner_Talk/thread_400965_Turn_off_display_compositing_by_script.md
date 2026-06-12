---
title: "Turn off display compositing by script"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Degeim on 2007-04-04
Hello

Im using XFCE (installed with Xubuntu and then upgraded to 4.4), and I'm sometimes playing Starcraft with my friends.

But I've noticed that it's kind of laggy if "Display compositing" is turned on (which it will be, since I love the effects). Therefore, I deactivate it before playing, and activate it again after.

But if someone could give me a script (I guess it is nothing more than to change something in some file, but I don't have the slightest clue of where to look), I could implement it in my .sh-file I use for launching the game anyway, so that I don't need to do it manually.

Does someone has the code for deactivating and reactivating display compositing?


Thanks,
Degeim

---

### Post by Skrynesaver on 2007-04-04
The file you are looking for is
/etc/X11/xorg.conf
With composite enabled do the following
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.composite-on
gksu gedit /etc/X11/xorg.conf

```enter your password in the editor search for "Composite" change the line to 
```
Option      "Composite" "Disable"
```save and close then
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.composite-off
```you now have two config files, you can swap between them by cp ing the composite-on or composite-off config over the current xorg.conf and restarting X CTRL-ALT-BKSPC

You could turn this into two scripts of the form
comp-off.sh
```

#! /bin/sh
sudo cp /etc/X11/xorg.conf.composite.off /etc/X11/xorg.conf

```
and comp-on.sh
```

#! /bin/sh
sudo cp /etc/X11/xorg.conf.composite.on /etc/X11/xorg.conf

```

---

### Post by Degeim on 2007-04-04
Yes! I should've checked the xorg.conf before I posted this.

But anyway, thank you!

---

