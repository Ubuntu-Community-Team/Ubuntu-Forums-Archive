---
title: "No Gyache Icon in Apps ??"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by gettinoriginal on 2007-03-12
When I log into Gyache, a little purple icon shows in the upper right of my top panel.  But in Applications, it only shows a blue bordered box.  When I try to add Gyache shortcut to the panel, I get an error message of "Gyache.png" not found,

---

### Post by Belyel on 2007-03-13
You can assign an icon to Gyachi by right clicking on "Applications" then selecting "Edit menus."  Use the interface and find the entry for Gyachi, right click on it select properties.  Click on the "no icon" place holder, and locate an icon for it.  I believe that if you installed it from the repositories, the icons will be: 
```
/usr/local/share/gyachi/pixmaps/gyach-icon_32.png
/usr/local/share/gyachi/pixmaps/gyach-icon_48.png
/usr/local/share/gyachi/pixmaps/gyvlogo.png

```

In the future, if you need to locate an icon for a program, I suggest using a terminal and typing
```
locate *programname* | grep .png
```

---

