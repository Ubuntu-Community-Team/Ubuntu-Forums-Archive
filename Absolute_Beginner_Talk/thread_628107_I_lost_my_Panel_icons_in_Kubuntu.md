---
title: "I lost my Panel icons in Kubuntu"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by OldDogNewTricks on 2007-11-30
In playing with the "Windows Appearance" configurations, I was trying to set a default window size for all applications.  The relative size setting can be remembered, and works okay.  But if I change one window, it remembers the setting for all windows.

So I foolishly chose the "Force Setting" option, thinking that would keep a given window size  for all windows.  Apparently, the force option really forces everything, including the icons on the panel. 'Cause it left me with a white panel with no visible icons.

I could fix it if I knew the terminal commands to reconfigure the windows appearance.  Because I cannot see the "System Settings" menu, I can't use a graphical interface to fix my problem.

I have a Ubuntu 7.10 installation with the KDE desktop added as a session option.  Uninstalling Kubuntu desktop manager and reinstalling it does not wipe out the config file, so that doesn't help either.  I really, really do not want to reinstall Ubuntu to fix this problem.

---

### Post by vikram on 2007-12-01
right click on any part of the empty panel and choose add Applet to panel. In the list of Panels you will see K Menu, that will give you access to system setting etc.

you may also want to add other applets like the clocks, multiple desktops etc. there should really be no need to reinstall anything including kubuntu-desktop. if you REALLY wanted to start with a clean slate you can delete the ".kde" dir under your home dir  but then you will loose all your settings, mail if you use kmail, addressbook if you use kaddressbook etc. if you do this *strongly* urge you to take a back up !!!

---

### Post by OldDogNewTricks on 2007-12-01
Problem Solved:

I tried the "right click and add" routine, but the panel remained blank.  Somehow my "force" order hosed it.  

So, after trying scores of things, like finding files that had changed in the past day, and looking at these for a configuration option, I decided to try everything I knew to get a K-menu to appear.  The trick was Alt-F1.  Once I had a K-menu it was trivial to go back to the System Options menu, reselect the Windows Appearance option, and delete my changes.  My Panel suddenly blossomed all its icons again.

I really do not understand why my reconfiguration of windows appearance would affect the panel, but it certainly did.  Beware the "force" option.

Anyway, thanks for the suggestions.

---

