---
title: "Non-package menu entries"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by tikbjamin on 2007-01-27
After updating the following packages this morning

Reading state information... Done
The following packages will be upgraded:
  app-install-data-commercial gnome-applets gnome-applets-data
  gnome-netstatus-applet gnome-panel gnome-panel-data gnome-system-tools
  libpanel-applet2-0 system-tools-backends


I noticed the following message as part of the output during the upgrade:

Caching application data...
Got non-package menu entry kiso.desktop
Got non-package menu entry k3dsurf.desktop
Got non-package menu entry xchm.desktop
Got non-package menu entry grdesktop.desktop
Got non-package menu entry tsclient.desktop
Got non-package menu entry brasero.desktop
Got non-package menu entry kmyfirewall.desktop
Generating mime map...

Question:
What does this mean?  Is this OK or normal (so many non-package menu entries)?

---

### Post by kerry_s on 2007-01-27
It means you don't have those installed so there not going to be added to the menu.

---

### Post by statecznik on 2007-07-24
I had the same messages. I'm curious why did they appear - I don't remember selecting any commercial programs. What is that app-install-data-commercial and what are those "non-package menu entries"? At first I was really concerned if that wasn't some sort of system break. Could anyone explain?

---

### Post by Mornedhel on 2007-07-24
Looks like this comes from update-app-install . I have no idea what it does, but it hasn't broken anything.

---

