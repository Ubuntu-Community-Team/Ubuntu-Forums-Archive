---
title: "Open as Root"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by islander_810 on 2007-02-26
I want a right-click option to open a directory with root privileges. How do i do it?

---

### Post by johnc4510 on 2007-02-26
sudo apt-get install nautilus-open-terminal

    * Nautilus -> Right-click on folder or background -> Open in Terminal

---

### Post by hanexar on 2007-02-26
I installed this with Automatix2 with a single click. You can give it a try : [http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by Kateikyoushi on 2007-02-26
This is how I did it, but did not use it.

Put the following into ~/.gnome2/nautilus-scripts/Open\ as\ root
Code:
#!/bin/sh
gksudo "gnome-open  $NAUTILUS_SCRIPT_SELECTED_URIS"
Then make it executable with
Code:
chmod +x ~/.gnome2/nautilus-scripts/Open\ as\ root

---

### Post by 23meg on 2007-02-26
You can use the attached Nautilus script. Make it executable and put it in your ~/.gnome2/nautilus-scripts folder.

---

### Post by islander_810 on 2007-02-26
Thx, it works. Is there any way to assign icons to this in the right-click menu, something like that for "Open in Terminal" ?

---

### Post by Kateikyoushi on 2007-02-27
What I wrote adds an Open as root line in the right click menu.

---

### Post by mcduck on 2007-02-27
> **islander_810 said:**
> Thx, it works. Is there any way to assign icons to this in the right-click menu, something like that for "Open in Terminal" ?

Just open the scripts directory, right-click your script, select 'Properties' and on the 'Basic'-tab you can select the icon for the file. This will also show in the right-click menu in Nautilus :)

---

### Post by islander_810 on 2007-02-27
hey, ya thx. that was pretty simple, stupid of me, not to think of that earlier :oops:

---

