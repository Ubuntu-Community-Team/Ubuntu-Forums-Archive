---
title: "Top, bottom panels not showing icons"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by bharkins on 2008-01-04
I have reviewed the previous threads to this topic, but not an answer that fits my situation. I have the panels, blank in white. If I hover the mouse, I get the tooltips that show the menus. However, I don't get any icons as normal. I've tried the various gnome-applets commands, but not solved. Any suggestions?

---

### Post by spydon on 2008-01-04
Try to right-click and add stuff, maybe you have just removed everything accidently... :P

---

### Post by bharkins on 2008-01-06
> **spydon said:**
> Try to right-click and add stuff, maybe you have just removed everything accidently... :P

Tried it but it didn't allow the icons to be relocated to the panel, a window shows only the menu of the icon, Applications, etc. I only get the tool tip by hovering over the panel. With open windows, if I minimize, they go to the bottom panel where I can see them by mouse cursor hovering. I'm looking for some sort of command to reset the Gnome desktop back to the default as when first installed.

---

### Post by spydon on 2008-01-06
Maybe this command...
```
sudo update-menus
```

---

### Post by Odd-rationale on 2008-01-06
This could be potentially dangerous, but you could try removing (move to trash so that you can restore if needed) your ~/.gconf/apps/panel directory. Gnome *should* put the default settings back when you log back in.

---

