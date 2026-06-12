---
title: "Workspace Desk error?"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by Sonastylol on 2008-02-02
Hey so last night I installed Ubuntu on my desktop, and an hour ago on my laptop. On the desktop, I found out ( since im a first time linux user ) that scrolling the mouse wheel will quickly go from one desk workspace to the other.

on a fresh laptop install, it does not. Whats the problem?

---

### Post by quimbo on 2008-02-02
Well I'm not sure as to whether or not you want this affect (though it does sound annoying).  
1) Check to see if you have ccsm installed.  You can do this one of two ways:
a - System->Preferences->Appearance->Visual Effects [tab]  if you see the Preferences Button your in business.

b - launch terminal and type ccsm.  If you get an error message, install it:
sudo apt-get install compizconfig-settings-manager

After it installs launch the program using one of the two fore mentioned ways (btw it's slow to launch on my machine so be patient).  Uncheck the setting 'Viewpoint Switcher.'  Close it!  That should work - I hope.

My guess as to why one does this and not the other...The visual effects is set to none in Appearance.

---

