---
title: "Edit as root - XFCE"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by dermotti on 2006-03-12
Is it possible to do a right-click edit as root or open root file browser like u can with gnome?

---

### Post by TrendyDark on 2006-03-12
I'm sure it is, but you'd have to add it to the right click menu. Not sure what you edit to have that edited.

---

### Post by Akli on 2006-03-12
How to browse files/folders as root user in Nautilus

    * Read #General Notes
    * To install File Browser (Root) 

sudo gedit /usr/share/applications/Nautilus-root.desktop

    *
          o Insert the following lines into the new file 

[Desktop Entry]
Name=File Browser (Root)
Comment=Browse the filesystem with the file manager
Exec=gksudo "nautilus --browser %U"
Icon=file-manager
Terminal=false
Type=Application
Categories=Application;System;

    *
          o Save the edited file
          o Read #How to refresh GNOME panel 

    * To browse files/folders as root user in Nautilus
          o Applications -> System Tools -> File Browser (Root) 


[http://easylinux.info/wiki/Ubuntu#How_to_browse_files.2Ffolders_as_root_user_in_Nautilus](http://easylinux.info/wiki/Ubuntu#How_to_browse_files.2Ffolders_as_root_user_in_Nautilus)

---

### Post by dermotti on 2006-03-13
I dont use nautilus, im trying to use THUNAR (XFCE browser) I guess i can try jsut replacing hte nautilus entry with thunar an see what happens...


Anyone know a graceful way to do this ?

---

### Post by marcotux on 2006-04-27
you can add a new customized action in thunar
open thunar: edit--->"custom action" and add "gksudo mousepad %f" for text file

bye;)

---

