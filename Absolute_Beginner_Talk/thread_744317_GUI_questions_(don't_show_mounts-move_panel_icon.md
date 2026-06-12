---
title: "GUI questions (don't show mounts-move panel icon"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by Agrajag27 on 2008-04-03
Slowing getting my feet wet. I just got Thunderbird to read my NTFS profile and have shared e-mail in both sessions. Very nice!

Anyway, first, is there a way to tell Ubuntu that I don't want mounted devices to appear on the desktop? I'd like to see these somewhere but NOT on my desktop.

Second, I added Thunderbird to my Panel so now next to "System" I have a Firefox icon, the Help icon and the Thunderbird icon. I'd like to move the Thunderbird icon to the left one spot but can't seem to do it. It can move all over to the right but I can't get this order changed. The first two icons also won't move at all.

---

### Post by forestpixie on 2008-04-03
Right click the other icons and unlock them so you can move your isons about

To not show volumes - do a Alt+F2 - in the run application put gconf-editor

Then navigate to apps > nautilus > dssktop and untick the volumes visible box and close

---

### Post by Slushdoot on 2008-04-03
As yourself type gconf-editor into a terminal window. Navigate Apps -> Nautilus -> Desktop. Untick the volumes_visible box.

---

