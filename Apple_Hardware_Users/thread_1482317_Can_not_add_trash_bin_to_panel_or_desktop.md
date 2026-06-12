---
title: "Can not add trash bin to panel or desktop"
date: 2010-05-13
forum: Apple Hardware Users
---

### Post by walterbyrd on 2010-05-13
When I try to add the trashbin to the panel, I get dozen icons appearing in my panel, then they go away. The same thing happens when I try to add a trash bin to my desktop.

---

### Post by ajgreeny on 2010-05-13
In which way are you trying to do this?

Apologies if I'm telling you what you already know, but for the desktop icon use ```
gconf-editor
``` in the Alt+F2 dialog and then go to apps ->nautilus ->desktop and set trash_icon_visible there, along with home and computer if you want them as well.

For the panel icon, right click in an empty part of the panel and choose Deleted items from the Add to Panel dialog.

---

