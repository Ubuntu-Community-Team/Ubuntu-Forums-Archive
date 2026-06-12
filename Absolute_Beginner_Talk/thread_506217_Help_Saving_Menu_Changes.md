---
title: "Help Saving Menu Changes"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by newbiefromwindows on 2007-07-21
I go system>Preferences>Main Menu, then I check the box of something I want to add to the menu. Now what? There is no apply box. If you close it simply reverts back to the way it was.

---

### Post by felicity on 2007-07-21
Sometimes it takes a restarting x (or your computer) for the menu to update your new preferences.

---

### Post by dptxp on 2007-07-21
This is the way. Should work.

---

### Post by testube_babies on 2007-07-21
Alacarte (the menu editor) has been broken on Ubuntu for quite some time.  It works well on all other distros I've tried, but I've never gotten it to work right since it was included by default in Ubuntu.

Strange, considering it was originally written FOR Ubuntu, that it is now just a source of frustration.

---

### Post by newbiefromwindows on 2007-07-21
> **testube_babies said:**
> Alacarte (the menu editor) has been broken on Ubuntu for quite some time.  It works well on all other distros I've tried, but I've never gotten it to work right since it was included by default in Ubuntu.

Strange, considering it was originally written FOR Ubuntu, that it is now just a source of frustration.

You're telling me the menu is broke?

---

### Post by testube_babies on 2007-07-21
> **newbiefromwindows said:**
> You're telling me the menu is broke?

Not exactly...it actually DOES work, it just doesn't work all of the time and it rarely works instantly.  You just have to be patient and keep trying until it does what you want.

---

### Post by newbiefromwindows on 2007-07-21
> **testube_babies said:**
> Not exactly...it actually DOES work, it just doesn't work all of the time and it rarely works instantly.  You just have to be patient and keep trying until it does what you want.

If I can't add items to the menu it does not work properly. Is this a known bug that is being fixed/how do I find that out?

---

### Post by Papi-KB7VGW on 2007-07-21
Wow I'm surprised because Main Menu works just fine for me.  The only time it doesn't work is if there are no programs in the group.  It wouldn't enable Debian until I had a file in there.  Other than that I can check and uncheck whatever and it works.

---

### Post by testube_babies on 2007-07-21
Here's how I usually have to add an application using Alacarte in Ubuntu:

1)  Right click menu -> 'Edit Menus'

2)  Select folder to add entry to, choose 'New Item' and create a new launcher.  Note that sometimes the Create Launcher dialog pops up BEHIND the Menu Editor window :mad:

3)  Hit OK and close alacarte.

4)  ALT+F2 and run **killall gnome-panel**

5)  When the panel reloads, check menus to see if new launcher showed up.  If it didn't, open alacarte and repeat.

Occasionally, I've had to restart X when moving launchers around to get them to show up in the right places.  Sometimes, launchers will show up in alacarte and not in the panel, and a system restart usually fixes that.

---

