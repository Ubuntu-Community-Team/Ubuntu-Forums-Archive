---
title: "Is there a Startup Folder?"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by zudduz on 2006-05-13
Is there a startup folder?  How do I make programs start running when I log on.

---

### Post by cowley on 2006-05-13
hi, you have to use sessions in the system>preferences

i.e. i have alltray start at boot up to load evolution by using:

alltray evolution

---

### Post by barbarian on 2006-05-13
hi,
in kubuntu there is directory .Autostart there you could place programs which should launched with startup.

---

### Post by scooper on 2006-05-13
Another way to autostart in Gnome is to add to the autostart list in the "Startup Programs" tab of the Sessions control panel applet.  You can get at it through the System/Preferences/Session menu item.  It's then independent of any sessions you want to save.

---

### Post by c2483 on 2006-12-07
any way to add something through cli

---

### Post by astoltz on 2006-12-07
You can add a "desktop" file to the ~/.config/autostart directory.

To make a new desktop autostart file,
```
cd ~/.config/autostart
nano application.desktop
```Then add the following to the file (change the specifics for the particular application your wanting to start):
```
[Desktop Entry]
Version=1.0
Type=Application
Name=Foo viewer
Comment=Foo comment!
Exec=fooview
StartupNotify=false
Terminal=false
Hidden=false

```

Edit:  I forgot to mention that support for this is relatively new in Gnome.  I know it works in Edgy, and am pretty sure about Dapper.  Before that, no promises.

---

