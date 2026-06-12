---
title: "Restore  Default Fonts?"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by adds2one on 2006-08-03
Is there a way to restore the fonts in Gnome to what they were on initial install?

---

### Post by aysiu on 2006-08-03
Try these three commands: ```
mv ~/.gconf/desktop/gnome/interface/%gconf.xml ~/.gconf/desktop/gnome/interface/%gconf.old.xml
mv ~/.gconf/apps/nautilus/preferences/%gconf.xml ~/.gconf/apps/nautilus/preferences/%gconf.old.xml
mv ~/.gconf/apps/metacity/general/%gconf.xml ~/.gconf/apps/metacity/general/%gconf.old.xml
``` You may have to log out and log back in again for the changes to take effect.

---

### Post by Hexx on 2006-08-03
The default font used is "Sans."

---

### Post by aesthete on 2008-02-04
Is there a similar command for KDE? I need to reset the font manager in systemsettings to the default fonts.

I think I may have deleted a core font package (I'm one of those crazy typeface people) and now NO special symbols are showing up (greek letters, bullet points). Well, they'll show up if I type it in myself, but opening a .doc or .ppt in Open Office shows symbols as missing character boxes. I've been trying for days to see if it's just my computer (it is), but I can't figure out which font package I deleted.

I have a lot of fonts still *installed* on the system, but I deleted them from the font manager in systemsettings, so I'm looking for a way to get them back.

---

