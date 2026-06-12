---
title: "All my drawers have vanished?"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by theacoustician on 2007-06-17
So, I've been using Ubuntu Studio on my laptop for about a week now.  I boot up this morning and find that all the drawers in my top panel (Applications, Places, System, etc.) are gone.  They've simply up and vanished.  The only thing there now is the help launcher.  So other than going through and manually rebuilding the default drawers and launchers, is there any quick way to restore the panel to default?  Thanks in advance.

---

### Post by ABCC on 2007-06-18
Youve got several options:

1. Put them back
Right-click on a panel, select 'Add to Panel' and add the 'Menu Bar'

2. Try wiping the gnome settings
Open a terminal and rename the gnome settings folders. Type 'mv .gnome2 .gnome2.old && mv .gnome .gnome.old'. This will force gnome to load it's default settings.

---

### Post by theacoustician on 2007-06-18
Ah!  Method 2 was what I was looking for.  I realized I could manually redo it all, but that seemed like it would take a lot of time.  Thanks so much.

---

### Post by ABCC on 2007-06-18
Well, the menu itself is contained within your .gnome2 folder if I'm not mistaken. The applet which your system wasn't displaying anymore (Apps,Places, Desktop) is optional. If you look in the Add Spplets menu youll find both that one and a main menu. Both of these read the installed programme information out of the .gnome2 folder. This means that even if you accidentally remove the applet, your menu will persist. Removing them will not affect the actual menu, just your ability to access it until you place another menu applet on your panels.

---

