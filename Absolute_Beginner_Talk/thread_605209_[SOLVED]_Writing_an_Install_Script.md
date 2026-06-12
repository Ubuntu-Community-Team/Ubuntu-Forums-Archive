---
title: "[SOLVED] Writing an Install Script"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by mdpalow on 2007-11-06
Hey Everyone,

can someone tell me where the file is located that holds the menu application stuff? Meaning, if I click on Applications -> Graphics -> and wanted to edit the Gimp menu item - where would I find the file it's written to?

I know I can edit it in System -> Preferences -> Main Menu, but I want to find the file that writes to.

Thanks in advance...


I FOUND IT.... Thanks anyways...

---

### Post by Dr Small on 2007-11-06
I find all of the application menu items in:
/usr/share/applications/

And here is a sample file:
```
[Desktop Entry]
Name=AVG Antivirus
Comment=Antivirus
Exec=gksudo avggui &
Icon=/opt/grisoft/avggui/prog/pixmaps/avgico_big.png
Terminal=false
Type=Application
Categories=Application;System;
```

And would be saved as avg.desktop

---

