---
title: "home folder shortcut"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by manutdfan2850 on 2007-01-05
how can i put a shortcut to my home folder on my desktop? 

thanks in advance

---

### Post by stimpack on 2007-01-05
In KDE:

right click desktop, select Create New->Link To location, click the browse folder then ok in the file dialog, ta da.

No idea for gnome.

---

### Post by livingtarget on 2007-01-05
In gnome:

Press ALT +F2 and type: gconf-editor

Now you should have the gnome configuration editor. Expand Apps -> Nautilus -> Desktop and check the box for home_icon_visible

There's things like trash etc. that you may want as well.

---

### Post by _simon_ on 2007-01-05
or alternatively, right click on your desktop.

Choose "create launcher"
Give it a name like "Home Folder"
The command will be /home/username
To give it an icon click on "no icon" and choose the one you want.
Press OK

**Obviously the username is your own.**

---

### Post by meng on 2007-01-05
I think there may even been the option of a keyboard shortcut to open the home folder
System > Prefs > Keyboard shortcuts.

---

### Post by manutdfan2850 on 2007-01-05
> **livingtarget said:**
> In gnome:

Press ALT +F2 and type: gconf-editor

Now you should have the gnome configuration editor. Expand Apps -> Nautilus -> Desktop and check the box for home_icon_visible

There's things like trash etc. that you may want as well.

thanks! :)

---

### Post by DRHamp on 2007-01-05
> **_simon_ said:**
> or alternatively, right click on your desktop.

Choose "create launcher"
Give it a name like "Home Folder"
The command will be /home/username
To give it an icon click on "no icon" and choose the one you want.
Press OK

**Obviously the username is your own.**

I did this and everything worked great until i tried to open the folder icon on the desktop.

I received an "error launching the application" message
Details: Failed to execute child process "/home/drhamp" (Permission denied)


Alternatively, I clicked on places in the top menu and dragged the Home folder to the desktop.

Is this the same thing?:-k

---

### Post by livingtarget on 2007-01-05
> **DRHamp said:**
> I did this and everything worked great until i tried to open the folder icon on the desktop.

I received an "error launching the application" message
Details: Failed to execute child process "/home/drhamp" (Permission denied)


Alternatively, I clicked on places in the top menu and dragged the Home folder to the desktop.

Is this the same thing?:-k

Actually do it my way it's a bit cleaner, but anyhow if you do want to do it like that:

Just do the same thing as he said, right click -> create launcher. Then make sure the dropdown box is set to FILE instead of application. Then type /home/drhamp as the command and that should be it.

---

### Post by DRHamp on 2007-01-05
> **livingtarget said:**
> Actually do it my way it's a bit cleaner, but anyhow if you do want to do it like that:

Just do the same thing as he said, right click -> create launcher. Then make sure the dropdown box is set to FILE instead of application. Then type /home/drhamp as the command and that should be it.

OK - that worked fine - I missed setting the type to "file" instead of the default "application"

How does the result differ from just dragging the home folder from the "places: menu to the desktop -- or is it different?

---

### Post by livingtarget on 2007-01-05
There's no difference in functionality, just whatever floats your boat. :D

EDIT: actually if you look at the properties they will look different if you set it by using the gnome configuration editor, just some useless trivia.

---

