---
title: "Wine Installation Issues"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by morwyn on 2006-03-27
I tried to install Wine & Winetools, but I am having a problem. For some reason, I am unable to install the Windows Installer. The installation keeps failing. Would it be better for me to uninstall Wine, download an earlier version, add winetools, make my installs and then update wine? If I should do that, how do I go about uninstalling wine, so I can try again with the earlier version?

---

### Post by gazj on 2006-03-27
Uninstall your wine, open a terminal (press alt+f2, then type gnome-terminal and press enter)

then type
```
sudo apt-get remove wine
```

to make sure your remove your old wine configuration files type

```
cd ~
rm -Rv .wine
```

Then
Follow my HOWTO :)

[http://www.ubuntuforums.org/showthread.php?t=149585]("http://www.ubuntuforums.org/showthread.php?t=149585")

---

