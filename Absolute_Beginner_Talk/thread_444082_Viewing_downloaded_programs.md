---
title: "Viewing downloaded programs"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by StevenP9891 on 2007-05-15
Why is it that when i download a lot of programs they dont show up under "application" in the menu bar. I either have to enter something in the terminal or search for it in the file mager. Is there a way to automatically place programs in the same place?

---

### Post by RomeReactor on 2007-05-15
Hi. Some times when you install a program, the panels need to be restarted for the application's entry to show up; to do that, go to "System-->Administration-->System Monitor", find **gnome-panel**, right-click on it and select "Kill Process" (don't worry; in the case of gnome-panel, that re-starts it). If the application you installed *does* have a menu entry, it will show up now. If it doesn't have an entry, then you'll have to make one by right-clicking on the "Applications    Places    System" menu on the top left and selecting "Edit Menus".

---

