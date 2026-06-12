---
title: "gnome customize menu"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by sankarv on 2007-04-18
i found that it is possible to customize the panel (simply right clicking and changing properties) in gnome where we can add/delete menus, launchers, workspaces, etc. But is it possible to change the color of the menu(s) added to panel or the fonts of those menus? please tell me how to do that. thankx in advance....

---

### Post by Obor on 2007-04-18
If you just want to change the colour of the panel you can use background image in the panel properties.

To change the colour of fonts and panel  plus the colour of the main menus etc you need to install/change GTK theme. You can find themes at [http://www.gnome-look.org](http://www.gnome-look.org) and install them in System - Preferences - Theme

---

### Post by ComplexNumber on 2007-04-18
> **sankarv said:**
> i found that it is possible to customize the panel (simply right clicking and changing properties) in gnome where we can add/delete menus, launchers, workspaces, etc. But is it possible to change the color of the menu(s) added to panel or the fonts of those menus? please tell me how to do that. thankx in advance....
or you could install [this]("http://3v1n0.tuxfamily.org/dists/edgy/3v1n0/") called gnome-color-chooser which gives you control over the colours of various parts of the desktop.

alternatively, you could add the following bit of code to your .gtk-2.0 file in your home directory to change the colours and font of the main menu and menubar (i'm not sure what menu you mean):
```

style "menu" {
 bg[NORMAL] = "#ff0000" # CHANGES THE BACKGROUND OF THE MENU TO RED
} 
class "GtkMenu" style "menu"


style "menu-item" {
 fg[NORMAL] = "#ffffff" # CHANGES THE TEXT COLOUR TO WHITE
 font_name = "Comic Sans MS Bold 14" #CHANGES FONT
}
class "*MenuItem*" style "menu-item"
```once you've inserted the code and saved the file, enter the following on the commandline for the changed to take effect:
killall gnome-panel

---

