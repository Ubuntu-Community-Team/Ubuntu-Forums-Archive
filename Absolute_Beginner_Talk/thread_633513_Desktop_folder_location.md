---
title: "Desktop folder location"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Odoacer on 2007-12-06
Weird problem here. I realized today that I had accidentally replaced my ~/Desktop folder with a text file (probably by misdirecting output when doing some programming) and the Desktop folder ended up in .Trash with no ill effects. This has been the case for several weeks.

Today I tried to restore the Desktop folder to its proper place, but for some reason gnome (or whatever) is treating ~ as my desktop folder, even though ~/Desktop exists. I've looked in apps/nautilus under gconf-edit and stuff, no luck in restoring. Any tips? Thanks.

---

### Post by kelbizzle on 2007-12-06
In Gconf edit. goto Edit -> Find . look in keynames for "desktop_is" . Or goto app/nautilus/preferences/desktop_is_home_dir . Is it checked? If so uncheck it and copy the stuff from the desktop in the trash.

---

### Post by Odoacer on 2007-12-06
No, desktop_is_home_dir is not checked. Checking and unchecking didn't help, either. Restarted in between checks to ensure everything was being read afresh.

---

### Post by crocuta on 2007-12-06
Hi. Last week i tried Miro on ubuntu 7.10. It crashed a lot, everytime settings would go back to default and when i uninstalled it   made a mess with my home and desktop folder.  

 So, now i'm at the same point that you are: the desktop shows my home folder, even when both ~Desktop and ~Escritorio (spanish for desktop, is the default name if you install in spanish)  exist. 

I tried the suggestion above, but does not work for me either.  I'll post back if i find a solution.

---

### Post by Odoacer on 2007-12-07
Bump, since this hasn't been solved yet.

---

