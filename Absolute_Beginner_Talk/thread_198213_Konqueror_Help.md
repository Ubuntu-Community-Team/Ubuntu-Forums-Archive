---
title: "Konqueror Help"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by Yggdrasill on 2006-06-16
I have accidentally removed the address bar and navigational buttons (back, forward, refresh, etc...) and don't know how to enable them again.  Is there a default button that will restore Konqueror to its original configuration?

---

### Post by lazyd2 on 2006-06-16
Open konqueror, go to Settings-->Configure Toolbars.

---

### Post by aysiu on 2006-06-16
[QUOTE=Yggdrasill]Is there a default button that will restore Konqueror to its original configuration?[/QUOTE] This terminal command should do it: ```
mv ~/.kde/share/apps/konqueror ~/.kde/share/apps/konqueror.old
```

---

### Post by Yggdrasill on 2006-06-17
[QUOTE=aysiu]This terminal command should do it: ```
mv ~/.kde/share/apps/konqueror ~/.kde/share/apps/konqueror.old
```[/QUOTE]

Didn't do anything...:confused:

---

### Post by aysiu on 2006-06-17
Did you try relaunching Konqueror afterwards?

**Edit**: Sorry. I just tested it. Wrong file/directory.

It should be this: ```
killall konqueror
mv ~/.kde/share/config/konquerorrc ~/.kde/share/config/konquerorrc.old
konqueror
```

---

