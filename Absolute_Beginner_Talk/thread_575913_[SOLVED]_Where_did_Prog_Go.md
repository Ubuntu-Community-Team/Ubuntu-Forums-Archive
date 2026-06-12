---
title: "[SOLVED] Where did Prog Go???"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Romin-1 on 2007-10-14
GDebi installed a Deb prog for me; Synaptic says that it is installed, "BUT", I cannot find it anywhere. It's not in any menu, in the Home Folder nor on the Desktop. It's a graphics tool.

How do I find it, Please?

Frustratedly,

Jon

---

### Post by llamakc on 2007-10-14
For starters how about telling us WHAT it was.

Next, you can figure out what files were installed with any deb by opening a terminal and typing:

dpkg -L nameofprogram

---

### Post by odiseo77 on 2007-10-14
Open synaptic, then look for the package, right click on it and click on 'Properties', then go to the 3rd tab (installed files or something like that); you should see one or more files inside '/usr/bin' or '/usr/local/bin' (these are more likely to be the directories, though the location may vary); these file(s) is/are the executable(s) one(s), so in a console, you could type: 

```
filename &
```

to see what happens.

Also, maybe the application added some menu entry, but is still not visible, you could try with ***killall gnome-panel*** to refresh the menu and look again.

Greetings.

---

### Post by zvacet on 2007-10-14
```
whereis package_name
```

or 

```
locate package_name
```

it is probably in usr/bin but look anyway.If it is not in dropdown menu applications>graphic right click on applications>edit menu>graphic>new item and make new launcher and type name of progran and command is where rhe progranm is (let say in usr/bin) and add icon.

---

### Post by Romin-1 on 2007-10-14
I managed to find a Python Script in user bin and opened it with terminal. Should say partly opened as terminal could not load all the libs.

The prog name is GursorMaker for X11 GTK+. Looked in Synaptic and am now at a loss of what to do since there are a lot of X11 files in there that aren't enabled. Phoooey,,

Thanks guys,

Jon

---

