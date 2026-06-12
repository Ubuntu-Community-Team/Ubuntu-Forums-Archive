---
title: "Programs not showing up in menu"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by Ryutatsu on 2006-05-21
After I install a program via synaptic or add aplication the program will not show up in the applications menu. Thinking I might have to put it there manually I launched smeg and to my suprise all of my prgrams were showing up in smeg but not in the actual menu. I've even restarted thinking that this would refresh the menu but it didn't change a thing. Does anyone have any ideas?

---

### Post by adamkane on 2006-05-21
You need to refresh the panel:
```

killall gnome-panel

```

Unfortunately some items have to be added manually.

See here for examples to add missing items to the start menu:
[http://easylinux.info/wiki/Ubuntu]("http://easylinux.info/wiki/Ubuntu")

Here's an example:

```

sudo gedit /usr/share/applications/azureus.desktop 

``` 
[FONT=monospace]```

[Desktop Entry] 
Name=Azureus
Comment=A Bittorrent client
Exec=/opt/azureus/azureus
Icon=/opt/azureus/Azureus.png
Terminal=false
Type=Application
Categories=Application;Network;

``` 
Save, and close.
[/FONT]

---

### Post by Ramses de Norre on 2006-05-21
Are the checkboxes in front of the applications in smeg checked?

---

### Post by Ryutatsu on 2006-05-21
Yes the boxes are checked I'll try re-adding the items but like I said they are already showing up in smeg.

Nevermind, re-adding the same entry worked

---

