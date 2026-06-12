---
title: "launcher to home folder"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by hwttdz on 2006-10-14
How can one make a launcher that opens file browser at the home directory?  Is there a tutorial on how to make launchers?  Thanks.

---

### Post by Perfect Storm on 2006-10-14
```
nautilus --no-desktop --browser %U
```

If it's for the panels; Just right click it choose add to panel and click add custom Application launcher.

---

### Post by IYY on 2006-10-14
If it's for the panel, just drag-and-drop from the Places menu.

If it's for the desktop, use the gconf configuration editor and check Home Folder under nautilus > desktop.

---

### Post by hwttdz on 2006-10-15
Drag and drop works for both the desktop and the panel.  For some reason right clicking doesn't work?? Right clicking opens the home folder and there's no way to get the menu that has add to panel as an option. Oh well, I have a working solution.  Thanks.

---

