---
title: "Loss of GUI followed by loss of touchpad and fn-key functionality"
date: 2008-02-07
forum: Apple Intel Users
---

### Post by profhomeslice on 2008-02-07
I've spent the past week getting 7.10 running on a new macbook. After finally getting everything up and running, I started to install software for work.

The next day when I booted the computer went straight to terminal. I fixed this by running  /etc/X11/xinit , and then when I rebooted the computer went back to the GUI as usual. Unfortunately, all the fixes I had done (double touch for right click, set up the fn key, etc) no longer worked. When I tried to repeat the fixes, nothing happened.

Any insight? Either to why the computer started going straight to the terminal in the first place or in how to get things fixed again? I'm trying to recall what I did before I started having the trouble. I installed wine and messed with a dll within that, and I also plugged in an apple usb mouse for the first time. Maybe that interfered with something?

I'm somewhat new to linux, thanks for the help.

---

### Post by prana on 2008-02-07
> **profhomeslice said:**
> I've spent the past week getting 7.10 running on a new macbook. After finally getting everything up and running, I started to install software for work.

The next day when I booted the computer went straight to terminal. I fixed this by running  /etc/X11/xinit , and then when I rebooted the computer went back to the GUI as usual. Unfortunately, all the fixes I had done (double touch for right click, set up the fn key, etc) no longer worked. When I tried to repeat the fixes, nothing happened.

Any insight? Either to why the computer started going straight to the terminal in the first place or in how to get things fixed again? I'm trying to recall what I did before I started having the trouble. I installed wine and messed with a dll within that, and I also plugged in an apple usb mouse for the first time. Maybe that interfered with something?

I'm somewhat new to linux, thanks for the help.

Before it went to the terminal, did it say that it could not start X?

From the grub menu, you could also try to start Ubuntu in failsafe mode and see if you get a GUI.

Once you have the GUI, you can try the command:

sudo dpkg-reconfigure -phigh xserver-xorg

from the terminal to start with a better X configuration.

---

### Post by profhomeslice on 2008-02-08
when i tried that and rebooted, a message popped up saying there was a conflict between gnome settings and x11, and to choose which one was correct. i said x11, and then the following error popped up

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10300000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

the result of xprop was:
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "macintosh", "us", "mac", "lv3:ralt_switch"
_XKB_RULES_NAMES(STRING) = "xorg", "apple_laptop", "us", "mac", "lv3:ralt_switch"

the result of gconftool was
 layouts = []
 model = 
 overrideSettings = true
 options = []

---

### Post by prana on 2008-02-09
> **profhomeslice said:**
> when i tried that and rebooted, a message popped up saying there was a conflict between gnome settings and x11, and to choose which one was correct. i said x11, and then the following error popped up

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10300000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

the result of xprop was:
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "macintosh", "us", "mac", "lv3:ralt_switch"
_XKB_RULES_NAMES(STRING) = "xorg", "apple_laptop", "us", "mac", "lv3:ralt_switch"

the result of gconftool was
 layouts = []
 model = 
 overrideSettings = true
 options = []

I think your system is hosed for some reason. The only thing I can suggest is to backup your data and reinstall Gutsy. Here is the guide that seems to be the most current though I haven't used it since I have a Macbook Pro. This guide is for the latest version of the Macbook.

[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

Good luck.

---

