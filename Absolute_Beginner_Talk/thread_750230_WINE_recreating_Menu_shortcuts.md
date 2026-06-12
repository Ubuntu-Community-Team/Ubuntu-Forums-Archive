---
title: "WINE: recreating Menu shortcuts"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by kneewax on 2008-04-09
I recently had to reinstall after accidentally deleting all my partitions (don't ask!) I managed to save some data and program settings and including my WINE folders.

I have reinstalled and copied the WINE app settings back to the /home folder. The programs work fine, but obviously don't show up in the WINE menu. Is there an easy way to get WINE to add the installed programs into the wine menus?

---

### Post by Confuzius on 2008-04-09
I'm pretty sure you'll have to do it by hand.
Settings/Preference/Main Menu (I think, I'm at work now)

First check and see if theres /.wine/c_drive/Documents and Settings\user\Start Menu\Programs

And see, you might be able to add that folder to your menu to get all of the installed wine programs (if it works like window)

Otherwise it's an entry for each application with "wine appname" to launch it.

---

