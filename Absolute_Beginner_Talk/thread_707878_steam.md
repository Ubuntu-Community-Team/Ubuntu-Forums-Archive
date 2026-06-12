---
title: "steam"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Lisa Y on 2008-02-25
how can i completely remove steam in wine... 

i used the...

sudo aptitude remove steam...but it didn't get removed...any help...please

---

### Post by PeterJS on 2008-02-25
The package management system only deals with native applications installed via package management. Everything installed by wine ends up in the fake windows directory located at ~/.wine/drive_c/. Given that the wine registry is non-critial to the system there's little incentive to keep it clean, you could just delete steam from the fake windows install. The shortcuts put in the menu are in: ~/.local/share/applications/wine/Programs/

---

### Post by JoshuaRL on 2008-02-25
You could also go into the Wine menu in Applications and chose Uninstall Programs.  It should bring up a list of all the stuff you've installed in Wine.  Choose the program and click the Uninstall button.

---

