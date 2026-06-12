---
title: "So I am a little OCD...Gnome Menu Issues"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by pbwalker on 2007-09-03
I am trying to manually delete some icons in my Menu. Unchecking it through the Menu Editor is not good enough for me. :)

I tried the menu config files in /.config, to no avail. How can I manually delete these entries through some config file? (Even right clicking and choosing delete isn't working)

---

### Post by darkenedday on 2007-09-03
I'm not sure what you want, you simply want to remove the menu entry and not the application? or just the icon an dleave the entry? or remove the app entirely?

---

### Post by pbwalker on 2007-09-03
> **darkenedday said:**
> I'm not sure what you want, you simply want to remove the menu entry and not the application? or just the icon an dleave the entry? or remove the app entirely?

The app is already removed. Yet, the menu icon still shows up when I am editing my menus (Through the Main Menu Editor)...and that is what I want to remove. I don't want to be reminded that I once had it installed...lol

---

### Post by Chris S. on 2007-09-03
When editing the menu, you can right click on the launcher icon and select delete.  Is that not what you want?

---

### Post by pbwalker on 2007-09-03
Sorry...I guess I am not being clear. 

Many moons ago, I installed a program, and deleted it a day or two later...

Tonight, while going to System --> Preferences --Main Menu (What I have referred to as the Menu Editor), I noticed under one of the submenus a checkmark and icon for that program that I had uninstalled. I will right click on it and choose "delete", it thinks for a second and then does nothing. I can't delete it through the menu editor. So I am looking for the manualy way of removing this reference, checkmark, and icon (so that when I am editing my main menu, it is not even visible)

I hoped that cleared it up.

---

### Post by Chris S. on 2007-09-03
Ah, I've had that problem before (or similar).  I usually resolved it by renaming the icon to something else or moving the icon to other folders, then altering it or deleting it.  I never figured out why that happened so maybe someone else knows more.

Just curious, but have you installed the Debian menu application (I think it's just the "menu" package?  I always suspected that was the cause of my problems.  I've never had the problem without it.

---

### Post by brentoboy on 2007-09-03
each menu item is a .desktop file, genereally stored in /usr/share/applications/*.desktop

they arent in a directory tree like the menu in windows, instead, they are all just there in one big directory, and the desktop file itself contains the application type that breaks them into categories in the menu.

im not entirely sure that all the menu items are in that exact directory, but that is where most of them seem to be.  Id start there and then search for all the .desktop files on the system.

---

