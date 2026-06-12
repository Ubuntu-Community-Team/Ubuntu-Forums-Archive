---
title: "2 Questions/Problems - Compiz and X Server"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by jeremycollins08 on 2008-03-29
Hi!

I have the compiz-config settings manager installed on ubuntu, and my computer can support all the effects that Compiz Fusion has to offer. There is, however, one problem. I really like what I've saw on demo videos of the water effects. I cannot seem to get the water effects to work. I enabled it, and set the keys to work, and when I click on "ctrl w" (thats what I set it to), it does nothing. The rain effects does not work, or any of the other effects of water works. Can someone help me get this working?


Ok, also, each time I log in to Ubuntu, a box comes up which reads:

```
The X system keyboard settings differ from your current GNOME keyboard settings.

Expected was model "pc101", layout "us" and no options, but the the following settings were found: model "pc105", layout "us" and no options.

Which set would you like to use?.
```

Your help is greatly apprechiated!

Thanks!

P.S. "I've already convinced 3 people to try linux...yay!"

---

### Post by jken146 on 2008-03-29
GNOME is the desktop environment you are using.  X server is the display system that does all the graphical (not text-based command line) display for you.

The settings for X are stored in /etc/X11/xorg.conf and include options for graphics drivers, screen resolution and keymaps.  You can change your X settings with the command ```
sudo dpkg-reconfigure xserver-xorg
```
GNOME also has keyboard settings.  Look in the System menu to change settings.

Ideally you want GNOME and X to have the same settings, or GNOME will keep on asking you which one is correct.

---

