---
title: "how to create menu items"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by drsyntax on 2007-06-25
i want to create a menu item for thunderbird 
wher i have to add this code ?
```
[Desktop Entry]
Encoding=UTF-8
Name=Thunderbird
Comment=Thunderbird Mail Client
Exec=thunderbird
Icon=/opt/thunderbird/icons/mozicon16.xpm
StartupNotify=true
Terminal=false
Type=Application
Categories=Applications;Network
```

---

### Post by p_quarles on 2007-06-25
Easy: click on System >> Preferences >> Main Menu. There you can check which items you want to show on the menu. You can create a desktop or panel launcher from the menu, once it's been added.

---

### Post by medley on 2007-06-25
> **drsyntax said:**
> i want to create a menu item for thunderbird 
wher i have to add this code ?
```
[Desktop Entry]
Encoding=UTF-8
Name=Thunderbird
Comment=Thunderbird Mail Client
Exec=thunderbird
Icon=/opt/thunderbird/icons/mozicon16.xpm
StartupNotify=true
Terminal=false
Type=Application
Categories=Applications;Network
```

If you want to add an item to your desktop menu, right-click on the 'K' (KDE) or the footprint (gnome) and select 'edit menu'. From there you should be able to figure out how to add a menu item. You may have to unlock your task bar first. If so, right-click and select this first.

---

### Post by drsyntax on 2007-06-25
can't i add this to a text file or something like that and save it and this will add an item automatically ??
because i don't know what to type in the command form, i wrote thunderbird but it didn't work

---

### Post by p_quarles on 2007-06-25
> **drsyntax said:**
> can't i add this to a text file or something like that and save it and this will add an item automatically ??
because i don't know what to type in the command form, i wrote thunderbird but it didn't work
Huh? If you follow the recommendations that medley and I gave you (which are slightly different, but amount to the same thing) it will "automatically" add the item. 

The only other way I know to do this is to right-click on the desktop, click "add launcher," type "Thunderbird" in the name field, and then type "mozilla-thunderbird" in the command field.

EDIT: If the "Thunderbird" option doesn't show up in "Edit Main Menu," though, then you probably don't even have it installed. If not, then open a terminal and type this: ```
sudo apt-get install mozilla-thunderbird
```

---

### Post by drsyntax on 2007-06-25
thx, i reinstall it and it works fine now

---

