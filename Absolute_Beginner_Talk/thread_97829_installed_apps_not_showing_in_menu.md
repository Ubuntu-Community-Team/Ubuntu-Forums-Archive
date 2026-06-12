---
title: "installed apps not showing in menu"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by rogerkint on 2005-12-01
I just installed scorched3d and celestia using SPM. They installed correctly and show up in the menu editor as being there and checked, but they aren't in the menu.  any help would be greatly appreciated.

R. Kint

---

### Post by rogerkint on 2005-12-01
actually, correction: scorched is showing up in the editor, celestia is not.

---

### Post by simgish on 2005-12-01
I don't believe Celestia sets a menu item by default but I could be wrong. Have you restarted gnome-panel?

---

### Post by rogerkint on 2005-12-01
yes, restarted whole comp, too... no luck.  is there a command line start for celestia?

---

### Post by jasay on 2005-12-01
There's command for everything. I have the gnome package of celestia installed so for me it's celestia-gnome.  If you don't know the command for a program you can try typing the first few letters and using tab once to attempt an autocomplete, twice to list all commands (or files in the working directory) that begin with those letters.

---

### Post by nitricacid on 2005-12-01
do you know where the app installed to and can you start the application?
If so just make a link of that file and place it in the /usr/share/applications folder.

---

### Post by canuck45 on 2005-12-02
[QUOTE=rogerkint]I just installed scorched3d and celestia using SPM. They installed correctly and show up in the menu editor as being there and checked, but they aren't in the menu.  any help would be greatly appreciated.

R. Kint[/QUOTE]

I had the same problem with several programes, showed in the menu editor with checkmark but not showing up in the menu.

I copied the command line from the program in the editor, removed the checkmark then selected NEW item, typed in the program name (ie. XYZ and description), pasted the command where i the command line area,  and then everything worked fine.  Showed up in the menus as XYZ

The autoinstall didn't work but when I did a second entry manually with the same info THAT one works fine.

---

