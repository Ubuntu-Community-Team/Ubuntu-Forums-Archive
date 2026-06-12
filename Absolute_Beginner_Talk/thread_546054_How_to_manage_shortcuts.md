---
title: "How to manage shortcuts"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by _d5 on 2007-09-08
Hi, 
I would like to get rid of the icons on my desktop of the mounted hdas, i would like to replace them with others, but i can not!

Please help!

---

### Post by tyggna1 on 2007-09-08
You might want to try unmouting them in nautilus.  To do so, go to places, and select "Home folder"  Then right click on the drive you want to get rid of and select unmount.

---

### Post by z0mbie on 2007-09-08
Press **ALT+F2** type in **gconf-editor** to open config-editor

Navigate to **apps > nautilus > desktop** and uncheck all the icons you want to remove. 

Then create new ones to point to where ever you want without editing the icon theme itself:

**Right Click** on **Desktop** > **Create Launcher...** and add the following to create a shortcut to a folder or a mounted device:

Command: 
```
nautilus /the/directory/you/want
```

Click on **No Icon** and select your custom icon.


There's a second method also, which requires you to edit the theme in your **~/.icons** directory of the current icon theme your using.

---

