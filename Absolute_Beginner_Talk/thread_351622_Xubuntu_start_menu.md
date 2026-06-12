---
title: "Xubuntu start menu"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by morequarky on 2007-02-02
my lunatic friend wants to re-name and re-sort items in xubuntu's app menu.

How would he change the name of "Network" to "Interent" for example?  Why? Please don't ask.

---

### Post by NewOldTimer on 2007-02-02
Don't know enough to lead you all the way, but here's a start

right click applications>properties>menu file/tick use custom menu file

---

### Post by pseudonym on 2007-02-02
> **NewOldTimer said:**
> Don't know enough to lead you all the way, but here's a start

right click applications>properties>menu file/tick use custom menu file
This will only change the menu layout, not the info for each menu entry.

Unfortunately, no one has written a good menu editor for xfce yet, but there is a way to get around this. Linux desktop environments are gradually trying to conform to the [Free Desktop]("http://www.freedesktop.org/wiki/") standard, which uses a predefined set of files for desktop menus. They all have the extension '.desktop' and reside in the /usr/share/applications directory (well, 95% of them anyway).

Each entry on the xfce menu has its corresponding .desktop file (if one doesn't, you can always create a custom one yourself). A basic custom example is this - ```
[Desktop Entry]
Name=Project X
Comment=DVB-Dateien bearbeiten
Exec=px
Icon=/media/data/bilder/icons/asst/media0.xpm
Type=Application
Categories=Application;AudioVideo;
```

To make the change you mention above, find the right .desktop file, open it up in a texteditor as sudo, then change the program/menu entry name, save and exit. The next time you browse the xfce menu things should be how you want them (though it may take a little while to register the change sometimes).

This is a kludge but unfortunately it's the way things are at the moment. You can read up a bit more about it if you want at the [website]("http://spuriousinterrupt.org/projects/xfce4") of one of the xfce4 developers (see the FAQ section).

HTH

---

